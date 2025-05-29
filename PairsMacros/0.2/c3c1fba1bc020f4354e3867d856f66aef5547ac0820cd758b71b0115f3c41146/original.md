Create Pairs expressions for use in `DataFrames.jl`

### Details

All symbols are assumed to refer to columns in the DataFrames, with the exception of:

  * `missing`
  * first `args` of a `:call` or `:.` expression (function calls)
  * arguments inside of a splicing/interpolation expression `$()` (refer to column names programatically).
  * arguments inside  `esc()` (refer to outside variables)

See also `@rows`

### Examples

```julia
julia> using PairsMacros
julia> @cols z = sum(x)
[:x] => sum => :z
julia> u = :y
julia> @cols z = sum($u)
[:y] => sum => :z
julia> @cols $u = sum(x)
[:x] => sum => :y
julia> @cols z = sum($"my variable name")
"my variable name" => sum => :z
julia> @cols z = map(esc(cos), y)
[:y] => (x -> map(cos, x)) => :z
```
