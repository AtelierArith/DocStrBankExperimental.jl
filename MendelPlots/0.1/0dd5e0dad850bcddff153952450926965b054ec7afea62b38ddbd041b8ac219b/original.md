```
manhattan(data::DataFrame)
```

# Position arguments

  * `data::DataFrame`: A DataFrame containing information to be used in the Manhattan Plot.

Note, DataFrame must have the following values saved under the corresponding names.  pvalues:pval, chromosome:chr. Additionally, the DataFrame must be in order of basepairs  going from first to last if there's no position arguement. Optionally, if there is  basepair information, then the position variable must be named `pos`. 

```
manhattan(pvalues::AbstractArray, chr::AbstractArray)
```

# Position arguments

  * `pvalues::AbstractArray`: pvalues for the associated GWAS. Must be in the

order of the basepairs. 

  * `chr::AbstractArray`: An array of chromosome identifiers for each pvalue.

Must match order with pvalues. 

```
manhattan(pvalues::AbstractArray, chr::AbstractArray, pos::AbstractArray)
```

# Position arguments

  * `pvalues::AbstractArray`: pvalues for the associated GWAS.

Must be in the same order of the basepairs and chromosomes. 

  * `chr::AbstractArray`: An array of chromosome identifiers for each pvalue.

Must match order with pvalues and positions. 

  * `pos::AbstractArray`: An array of basepair positions for each pvalue/chromosome.

Must match order with pvalues and chromosomes. 

# Keyword arguments

  * `titles::AbstractString`: Title for the plot. Default is "Manhattan Plot".

To have blank enter "". 

  * `outfile::AbstractString`: output name to save the manhattan plot. Name should end in format.

Default is "manhattan.png". Supports .png, .pdf, and .svg files. 

  * `dpi::Int64`: dots per inch to save the png file. Higher DPI results in

larger file with higher resolution. Default dpi is 350.

  * `xlabel::AbstractString`: option to replace x-label text
  * `ylabel::AbstractString`: option to replace y-label text
  * `ymax::Union{Float64, Int64}`: Specified maximum y value to represent

on the plot

  * `ystep`: Step-size for y-axis label ticks. Default value is 2.5
  * `signifline::Union{Float64, Int64}`: Line to draw significance at.

Default in Bonferonni corrected p-value for α = 0.05. 

  * `linecolor::AbstractString`: Color for significance line. Default

is 'deepskyblue1'. 

  * `fontsize` size of the axis labels. Default is "15pt".
  * `pvalvar` variable indicating pvalue column name (for dataframes only). Default is "pval".
  * `chrvar` variable indicating chromosome column name (for dataframes only). Default is "chr".
  * `posvar` variable indicating BP position column name (for dataframes only). Default is "pos".
  * `annotatevar` variable indicating annotation column name (for dataframes only). Default is "gene".
  * `annotateinds` indicies of rows to include as annotation for the manhattan plot. Default is `nothing`.
