```
parsemiss(Q, x::Vector{Union{String, Missing}})
```

Parsing a string vector allowing missing data.

  * `Q` : Type that results from the parsing of type `String'.
  * `x` : A string vector containing `missing` (of type `Missing`)    observations.

See examples.

## Examples

```julia
using Jchemo

x = ["1"; "3.2"; missing]
x_p = parsemiss(Float64, x)
```
