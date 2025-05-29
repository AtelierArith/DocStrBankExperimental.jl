```
tableone(data, strata[, vars]; <keyword arguments>)
```

Produce a summary table which may be used as Table 1 in a manuscript.

## Arguments

  * `data`: A `DataFrame` containing the data to be included in the table
  * `strata`: The variable (a column in `data`) by which the data should be stratified    in the table
  * `vars`: The variables to be listed in the table, defaults to `Symbol.(names(data))`    if not supplied

# Keyword arguments

## Types of variables

Each of these must be supplied as the same type as `vars`, e.g. if `vars` is a `Vector{Symbol}`      then these should each be a `Vector{Symbol}`. Variables supplied to one of these      arguments but not the main `vars` argument will not be displayed.

  * `binvars`: binary variables – variable will take one row and show **number (%)**    with the selected level (see `binvardisplay` below)
  * `catvars`: categorical variables – each level in the variable will be shown on    a separate line with the **number (%)** in that category
  * `npvars`: non-parametric variables – will display **median [1st–3rd quartiles]**
  * `paramvars`: parametric variables – will display **mean (standard deviation)**
  * `cramvars`: a variation of `binvars` that displays both levels in one row on the table

Any variables not included in one of these arguments will be presented as      `mean (standard deviation)` if the contents of the variable are      `<:Union{<:Number, Missing}`, and as categorical otherwise.

## Additional keyword arguments

  * `addnmissing=true`: include the numer of records with missing values for each    variable. If `true`, will also display number with missing `strata` values
  * `addtestname=false`: show the name of the statistical test used to calculate    p-values. This option has no effect unless `pvalues == true`
  * `addtotal=false`: include a column of totals across all `strata`
  * `binvardisplay=nothing`: optionally, a `Dict` to choose the level to display    for binary values. Any variables not listed will use the value chosen by    `maximum(skipmissing(.))`
  * `digits=1`: number of digits to be displayed after the decimal place in means,    standard deviations and percentages
  * `includemissingintotal=false`: include records with missing stratification variable    in the totals column. This option has no effect if `addtotal == false`
  * `pdigits=3`: number of digits to be displayed after the decimal place for p-values
  * `pvalues=false`: whether to display significant test p-values for each variable    in the table
  * `varnames=nothing`: optionally, a `Dict` of names for variables different    from the column titles in `data`, of the form `Dict(:columnname => "name to print")`.    Any variables not included will be listed by the column name

See documentation for examples.
