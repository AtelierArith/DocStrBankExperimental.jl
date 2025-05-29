```
tablequartetCF(quartetlist::Vector{QuartetT} [, taxonnames];
               keepQwithoutgenes=true, colnames=nothing)
```

Convert a vector of [`QuartetT`](@ref) objects to a table with 1 row for each four-taxon set in the list. Each four-taxon set contains quartet data of some type `T`, which determines the number of columns in the table. This data type `T` should be a vector of length 3 or 4, or a 3×n matrix. The output is a `NamedTuple`, to which we can apply common table operations as a [`Table.jl`](https://github.com/JuliaData/Tables.jl)-compatible source. It can easily be converted to other table formats (e.g. these packages [integrate with Tables.jl](https://github.com/JuliaData/Tables.jl/blob/master/INTEGRATIONS.md)) such as a `DataFrame`.

In the output table, the columns are, in this order:

  * `qind`: contains the quartet's `number`
  * `t1, t2, t3, t4`: contain the quartet's `taxonnumber`s if no `taxonnames` are given, or the taxon names otherwise. The name of taxon number `i` is taken to be `taxonnames[i]`.
  * 3 or more columns for the quartet's `data`: see [`quartetdata_columnnames`](@ref).

In short, the first 3 columns of data are named `CF12_34, CF13_24, CF14_23`.

If quartets have 4 data entries, then the 4th column is named `ngenes`, and a quartet with a value `ngenes` of 0 is skipped (excluded) from the table, unless `keepQwithoutgenes=true` (which is the default: 4-taxon sets are kept by default even without any informative genes).

If quartets have a data matrix with 3 rows and `d` columns, then the columns 4,5,6 in the table are named `V2_12_34, V2_13_24, V2_14_23` and contain the data in the second column of the quartet's data matrix. And so on.

For the table to have non-default column names, provide the desired 3, 4, or 3×d names as a vector via the optional argument `colnames`.

See [`countquartetsintrees`](@ref) for examples.
