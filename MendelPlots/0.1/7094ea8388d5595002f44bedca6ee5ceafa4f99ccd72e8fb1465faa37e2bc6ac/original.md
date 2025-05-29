```
qq(pvalues::AbstractArray)
```

# Position arguments

  * `pvalues::AbstractArray`: pvalues. A one dimensional array containing pvalues to be used in the qqplot.

    qq(df::DataFrame)

# Position arguments

  * `df::DataFrame`: DataFrame containing pvalues to be used in the qqplot. Note: The column of the dataframe

that indicates pvalues must be named pval (df[!, :pval] must exist)

# Keyword arguments

  * `titles::AbstractString`: Title for the plot. Default is "QQ Plot of GWAS p-values".

To have blank enter "". 

  * `outfile::AbstractString`: output name to save the QQplot. Name should end in format.

Default is "qqplot.png". Supports .png, .pdf, and .svg files. 

  * `dpi::Union{Float64, Int64}`: dots per inch to save the png file. Higher DPI results in larger file with

higher resolution. Default dpi is 350.

  * `xlabel::AbstractString`: option to replace x-label text
  * `ylabel::AbstractString`: option to replace y-label text
  * `xmin::Union{Float64, Int64}`: Specified minimum x value to represent on the plot
  * `xmax::Union{Float64, Int64}`: Specified maximum x value to represent on the plot
  * `ymin::Union{Float64, Int64}`: Specified minimum y value to represent on the plot
  * `ymax::Union{Float64, Int64}`: Specified maximum y value to represent on the plot
  * `xstep`: Step-size for x-axis label ticks. Default value is 1.
  * `ystep`: Step-size for y-axis label ticks. Default value is 2.
  * `gifdist`: Distance from right edge to print the genomic inflation factor `λ`. Default is 1.0.
  * `linecolor::AbstractString`: Color of "normal" line. Default color is "red".
  * `dotcolor::AbstractString`: Color of the dots. Default color is "black".
  * `fontsize` size of the axis labels. Default is "15pt".
  * `pvalvar` variable indicating pvalue column name (for dataframes only). Default is "pval".
