# Correlation Matrix

**ID**: `correlation-matrix`  
**Version**: 1.0.0  
**Category**: visualization  
**Author**: CauldronGO Team

## Description

Generate correlation matrices with customizable visualization options

## Runtime

- **Type**: `r`
- **Script**: `correlation_matrix.R`

## Inputs

| Name | Label | Type | Required | Default | Visibility |
|------|-------|------|----------|---------|------------|
| `input_file` | Input File | file | Yes | - | Always visible |
| `index_col` | Index Column | text | No | - | Always visible |
| `sample_cols` | Sample Columns | column-selector (multiple) | Yes | - | Always visible |
| `method` | Correlation Method | select (pearson, spearman, kendall) | No | pearson | Always visible |
| `min_value` | Minimum Value | number | No | 0 | Always visible |
| `order` | Order | select (original, AOE, FPC, hclust, alphabet) | No | - | Always visible |
| `hclust_method` | Hierarchical Clustering Method | select (ward.D, ward.D2, single, complete, average, mcquitty, median, centroid) | No | ward.D | Always visible |
| `presenting_method` | Presentation Method | select (circle, square, ellipse, number, shade, color, pie) | No | ellipse | Always visible |
| `cor_shape` | Correlation Shape | select (full, upper, lower) | No | upper | Always visible |
| `plot_only` | Plot Only (Skip Correlation) | boolean | No | false | Always visible |
| `color_ramp_palette` | Color Palette | text | No | - | Always visible |
| `plot_width` | Plot Width | number (min: 5, max: 30) | No | 10 | Always visible |
| `plot_height` | Plot Height | number (min: 5, max: 30) | No | 10 | Always visible |
| `text_label_size` | Text Label Size | number (min: 0, max: 5, step: 0) | No | 1 | Always visible |
| `number_label_size` | Number Label Size | number (min: 0, max: 5, step: 0) | No | 1 | Always visible |
| `label_rotation` | Label Rotation | number (min: 0, max: 90, step: 5) | No | 45 | Always visible |
| `show_diagonal` | Show Diagonal | boolean | No | true | Always visible |
| `add_grid` | Add Grid | boolean | No | false | Always visible |
| `grid_color` | Grid Color | text | No | black | Always visible |
| `number_digits` | Number of Digits | number (min: 0, max: 5, step: 1) | No | 2 | Always visible |
| `plot_title` | Plot Title | text | No | - | Always visible |
| `use_basename` | Use Basename Only | boolean | No | true | Always visible |
| `max_label_length` | Max Label Length | number (min: 10, max: 200, step: 5) | No | 50 | Always visible |

### Input Details

#### Input File (`input_file`)

Data file for correlation analysis


#### Index Column (`index_col`)

Column name to use as row identifier


#### Sample Columns (`sample_cols`)

Columns to include in correlation analysis

- **Column Source**: `input_file`

#### Correlation Method (`method`)

Method for calculating correlations

- **Options**: `pearson`, `spearman`, `kendall`

#### Minimum Value (`min_value`)

Minimum value for filtering


#### Order (`order`)

Ordering method for variables

- **Options**: `original`, `AOE`, `FPC`, `hclust`, `alphabet`

#### Hierarchical Clustering Method (`hclust_method`)

Method for hierarchical clustering

- **Options**: `ward.D`, `ward.D2`, `single`, `complete`, `average`, `mcquitty`, `median`, `centroid`

#### Presentation Method (`presenting_method`)

Visual representation of correlations

- **Options**: `circle`, `square`, `ellipse`, `number`, `shade`, `color`, `pie`

#### Correlation Shape (`cor_shape`)

Which part of the matrix to display

- **Options**: `full`, `upper`, `lower`

#### Plot Only (Skip Correlation) (`plot_only`)

Plot the input data directly without computing correlations


#### Color Palette (`color_ramp_palette`)

Color palette for the plot

- **Placeholder**: `RdYlBu,Blues,Greens`

#### Plot Width (`plot_width`)

Width of the plot in inches


#### Plot Height (`plot_height`)

Height of the plot in inches


#### Text Label Size (`text_label_size`)

Size of text labels


#### Number Label Size (`number_label_size`)

Size of correlation coefficient numbers


#### Label Rotation (`label_rotation`)

Rotation angle for labels in degrees


#### Show Diagonal (`show_diagonal`)

Show the diagonal of the correlation matrix


#### Add Grid (`add_grid`)

Add grid lines to the plot


#### Grid Color (`grid_color`)

Color of grid lines (if enabled)


#### Number of Digits (`number_digits`)

Decimal places for correlation coefficients


#### Plot Title (`plot_title`)

Title for the correlation plot


#### Use Basename Only (`use_basename`)

Extract only the filename from full file paths


#### Max Label Length (`max_label_length`)

Maximum length for axis labels (characters)


## Outputs

| Name | File | Type | Format | Description |
|------|------|------|--------|-------------|
| `correlation_matrix` | `correlation_matrix.txt` | data | tsv | Correlation matrix values |
| `correlation_plot_pdf` | `correlation_matrix.pdf` | image | pdf | Correlation matrix visualization (PDF) |
| `correlation_plot_svg` | `correlation_matrix.svg` | image | svg | Correlation matrix visualization (SVG) |

## Visualizations

This plugin generates 1 plot(s):

### Correlation Matrix (`correlation_plot`)

- **Type**: image-grid
- **Data Source**: `correlation_plot_svg`
- **Image Pattern**: `*.svg`

## Requirements

- **R**: >=4.0
- **Packages**:
  - corrplot
  - RColorBrewer

## Example Data

This plugin includes example data for testing:

```yaml
  sample_cols_source: diann/imputed.data.txt
  sample_cols: [C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_01.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_02.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_03.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_01.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_02.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_03.raw]
  index_col: Precursor.Id
  method: pearson
  hclust_method: ward.D
  presenting_method: ellipse
  cor_shape: upper
  order: hclust
  color_ramp_palette: #053061,#2166AC,#4393C3,#92C5DE,#D1E5F0,#FFFFFF,#FDDBC7,#F4A582,#D6604D,#B2182B,#67001F
  use_basename: true
  max_label_length: 50
  input_file: diann/imputed.data.txt
```

Load example data by clicking the **Load Example** button in the UI.

## Usage

### Via UI

1. Navigate to **visualization** → **Correlation Matrix**
2. Fill in the required inputs
3. Click **Run Analysis**

### Via Plugin System

```typescript
const jobId = await pluginService.executePlugin('correlation-matrix', {
  // Add parameters here
});
```
