```
expandsampledata(x, experiment[, colnames])
```

Return a DataFrame containing the sample data for all or some of the column names in the chosen `experiment`. Columns are the same as those in `sampledata(x)`.

If `colnames` is supplied, each row of the returned `DataFrame` corresponds to an entry of `colnames` and contains the data for the sample matching that column in the specified experiment.

If `colnames` is not supplied, each row of the returned `DataFrame` corresponds to a column of the specified experiment.

An error is raised if the requested columns do not have a matching sample in `samplemap(x)`.  Use [`dropunused`](@ref) to remove unused columns from each experiment prior to calling this function.

A warning is raised if `sampledata(x)` contains duplicate sample names. In such cases, data is taken from the first entry for each sample.

A warning is raised if `samplemap(x)` contains multiple occurrences of the same experiment/colname combination with a different sample. In such cases, the first occurrence of the combination is used.

# Examples

```jldoctest
julia> using MultiAssayExperiments;

julia> x = MultiAssayExperiments.exampleobject();

julia> expandsampledata(x, "foo")
10×2 DataFrame
 Row │ name      disease 
     │ String    String  
─────┼───────────────────
   1 │ Patient1  good
   2 │ Patient1  good
   3 │ Patient1  good
   4 │ Patient2  bad
   5 │ Patient2  bad
   6 │ Patient2  bad
   7 │ Patient3  good
   8 │ Patient3  good
   9 │ Patient3  good
  10 │ Patient4  bad

julia> expandsampledata(x, "foo", ["foo2", "foo1"])
2×2 DataFrame
 Row │ name      disease 
     │ String    String  
─────┼───────────────────
   1 │ Patient1  good
   2 │ Patient1  good
```
