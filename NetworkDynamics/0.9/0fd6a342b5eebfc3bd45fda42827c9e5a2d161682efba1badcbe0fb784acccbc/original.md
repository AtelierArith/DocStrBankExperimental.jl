```
NWParameter(nw_or_nw_wraper, pflat)
```

Indexable wrapper for flat parameter array `pflat`. Needs Network or wrapper of Network, e.g. `ODEProblem`.

```
p = NWParameter(nw)
p.v[idx, :sym] # get parameter :sym of vertex idx
p.e[idx, :sym] # get parameter :sym of edge idx
p[s::Union{VPIndex, EPIndex}] # get parameter for specific index
```

Get flat array representation using [`pflat`](@ref). The order of parameters in the flat representation corresponds to the order given by [`parameter_symbols`](@ref).
