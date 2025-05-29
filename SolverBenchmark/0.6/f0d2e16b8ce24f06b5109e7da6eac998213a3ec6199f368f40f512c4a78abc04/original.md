```
df = join(stats, cols; kwargs...)
```

Join a dictionary of DataFrames given by `stats`. Column `:id` is required in all DataFrames. The resulting DataFrame will have column `id` and all columns `cols` for each solver.

Inputs:

  * `stats::Dict{Symbol,DataFrame}`: Dictionary of DataFrames per solver. Each key is a different solver;
  * `cols::Array{Symbol}`: Which columns of the DataFrames.

Keyword arguments:

  * `invariant_cols::Array{Symbol,1}`: Invariant columns to be added, i.e., columns that don't change depending on the solver (such as name of problem, number of variables, etc.);
  * `hdr_override::Dict{Symbol,String}`: Override header names.

Output:

  * `df::DataFrame`: Resulting dataframe.
