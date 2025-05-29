```
rcall{T}(e::T)
```

Evaluate a Julia expression or string using the Reduce interpretor and convert output back into the input type

## Examples

```julia-repl
julia> rcall("int(sin(y)^2, y)")
"( - cos(y)*sin(y) + y)/2"

julia> rcall(:(int(1/(1+x^2), x)))
:(atan(x))
```
