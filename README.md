
<!-- README.md is generated from README.Rmd. Please edit that file -->

# scrubletR

<!-- badges: start -->
<!-- badges: end -->

scrubletR is an R package designed to run Python's Scrublet package via reticulate. [Scrublet](https://pypi.org/project/scrublet/) gathers metadata summarising potential doublet cells in Single Cell RNA-seq experiments.

This fork of [Moonerss/scrubletR](https://github.com/Moonerss/scrubletR) includes some bug fixes, improving compatability with Seurat v5

## Installation

You can install the master branch of this [Github](https://github.com/ofarrelle/scrubletR) repository with:

``` r
remotes::install_github("ofarrelle/scrubletR")
```

## Prerequisites

-   R package: Matrix, reticulate, Seurat

-   Python module: scrublet

## Using

``` r
load("~/samples.RData")
res <- scrublet_R(seurat_obj = samples)
# Preprocessing...
# Simulating doublets...
# Embedding transcriptomes using PCA...
# Calculating doublet scores...
# Automatically set threshold at doublet score = 0.57
# Detected doublet rate = 0.1%
# Estimated detectable doublet fraction = 0.6%
# Overall doublet rate:
#   Expected   = 6.0%
#   Estimated  = 12.1%
# Elapsed time: 32.5 seconds
```

``` r
head(res@meta.data)
#                       orig.ident nCount_RNA nFeature_RNA percent.mt
# AAACCCAAGAGTCACG-1 SeuratProject       5985         1844   7.552214
# AAACCCAAGCCGTCGT-1 SeuratProject      11923         2532  11.725237
# AAACCCAAGGACACTG-1 SeuratProject       1728          783  22.858796
# AAACCCACAAAGGTTA-1 SeuratProject      10676         2649  22.798801
# AAACCCACAGACGCTC-1 SeuratProject       2235          690  55.078300
# AAACCCACAGGAACCA-1 SeuratProject      14519         3402   4.979682
#                    doublet_scores predicted_doublets
# AAACCCAAGAGTCACG-1     0.01636424              FALSE
# AAACCCAAGCCGTCGT-1     0.03400332              FALSE
# AAACCCAAGGACACTG-1     0.22724604              FALSE
# AAACCCACAAAGGTTA-1     0.02451680              FALSE
# AAACCCACAGACGCTC-1     0.01955671              FALSE
# AAACCCACAGGAACCA-1     0.01955671              FALSE
```
