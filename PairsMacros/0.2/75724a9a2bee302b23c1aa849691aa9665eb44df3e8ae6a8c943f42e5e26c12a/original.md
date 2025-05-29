Create Pairs expressions for use in `DataFrames.jl`, where the function is enclosed by `ByRow`

### Details

All symbols are assumed to refer to columns in the DataFrames, with the exception of:

  * `missing`
  * first `args` of a `:call` or `:.` expression (function calls)
  * arguments inside of a splicing/interpolation expression `$()` (refer to column names programatically).
  * arguments inside  `esc` (refer to outside variables)

See also `@cols`

### Examples

```julia
using PairsMacros
julia> @rows z = abs(x)
[:x] => ByRow(abs) => :z
julia> @rows z = tryparse(esc(Float64), x)
[:x] => (x -> tryparse(Float64, x) => :z
```
