```
P_str(s)
```

(Unitful extension only). Creates a string that will be Protected from recipe passes.

Example:

```julia
julia> using Unitful
julia> plot([0,1]u"m", [1,2]u"m/s^2", xlabel=P"This label will NOT display units")
julia> plot([0,1]u"m", [1,2]u"m/s^2", xlabel="This label will display units")
```
