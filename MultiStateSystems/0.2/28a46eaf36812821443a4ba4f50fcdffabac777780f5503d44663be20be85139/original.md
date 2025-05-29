```
UGF
```

An ugf is a struct containing: a measure `msr`, corresponding values `val` and  associated probabilities `prb`, with default constructor: 

```
UGF(msr::Symbol, val::Vector, prb::Vector; red::Bool=true)
```

A UGF constructor for a specific measure `msr` based on a given value vector  `val` and associated probability vector `prb`.

This function automatically reduces the state-space to where only unique values and associated probabilites remain. This behavior is circumvented by passing the optional argument `rdc=false`.

# Example

```julia-repl
julia> ugfᵍᵉⁿ = UGF(:power, [0.0u"MW",0.0u"MW",2.0u"MW"], [0.1,0.2,0.7])
julia> isequal(ugfᵍᵉⁿ.val, [0.0u"MW",2.0u"MW"])
true
julia> ugfᵍᵉⁿ = UGF(:power, [0.0u"MW",0.0u"MW",2.0u"MW"], [0.1,0.2,0.7], rdc=false)
julia> isequal(ugfᵍᵉⁿ.val, [0.0u"MW",0.0u"MW",2.0u"MW"])
true
```
