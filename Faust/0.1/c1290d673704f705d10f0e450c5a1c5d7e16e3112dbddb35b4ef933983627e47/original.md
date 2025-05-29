```
setparams!(d, params)
```

Sets the parameters on `d` using keys from `params`.

One can extract the available params as UIRange structs from `d.ui.ranges` after iniialization.

# Examples

```julia-repl
julia> d = init!(compile("process = nentry("v", 0, 0, 1, 0.001);"))
julia> d.ui.ranges
Dict{String, Faust.UIRange} with 1 entry:
  "/score/v" => UIRange(0.0, 0.0, 1.0, 0.001)
julia> setparams!(d, Dict("/score/v" => 0.5f0))
```
