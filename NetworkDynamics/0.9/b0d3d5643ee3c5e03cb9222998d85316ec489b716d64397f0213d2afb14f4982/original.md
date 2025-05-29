```
NWState(nw_or_nw_wrapper, uflat, [pflat], [t])
```

Indexable wrapper for flat state & parameter array. Needs Network or wrapper of Network, e.g. `ODEProblem`.

```
s = NWState(nw)
s.v[idx, :sym] # get state :sym of vertex idx
s.e[idx, :sym] # get state :sym of edge idx
s.p.v[idx, :sym] # get parameter :sym of vertex idx
s.p.e[idx, :sym] # get parameter :sym of edge idx
s[s::Union{VIndex, EIndex, EPIndex, VPIndex}] # get parameter for specific index
```

Get flat array representation using [`uflat`](@ref) and [`pflat`](@ref). The order of states in the flat representation corresponds to the order given by [`variable_symbols`](@ref), and the order of parameters corresponds to [`parameter_symbols`](@ref).
