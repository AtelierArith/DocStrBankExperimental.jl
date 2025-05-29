```
filewriter(path::AbstractString, ds::AbstractDataset; [...])
```

Write `ds` as text to a file (`path`) using the given delimiter `delimiter` (which defaults to comma). User can pass a single character or a vector of characters to the `delimiter` keyword argument.

# Keyword arguments

  * `delimiter`: By default, `filewriter` uses comma as delimiter, however, user can pass any other `Char` (or a vector of `Char`) via the `delimiter` keyword argument.
  * `mapformats`: Setting this as `true` causes `filewriter` to write the formatted values.
  * `append`: Setting this as `true` causes `filewriter` to append values to the end of the input file.
  * `header`: The `filewriter` function writes column names in the output file, however, this can be prevented by setting `header = false`.
  * `buffsize`: This option controls the buffer size.
  * `lsize`: This option controls the line size for writing values.
  * `threads`: If set `true`, `filewriter` exploits all threads.

# Example

```julia
julia> using InMemoryDatasets

julia> ds = Dataset(x=[1.0, 2.1, -2.0], y = 1:3)
3×2 Dataset
 Row │ x         y        
     │ identity  identity 
     │ Float64?  Int64?   
─────┼────────────────────
   1 │      1.0         1
   2 │      2.1         2
   3 │     -2.0         3

julia> filewriter("_tmp.csv", ds)
```
