```
UGF(msr::Symbol, std::MultiStateSystems.AbstractSTD)
```

A UGF constructor for a specific measure `msr` based on a given state-transition diagram `std`.

This function automatically reduces the state-space to where only unique values and associated probabilites remain.

# Example

```julia-repl
julia> stdᵍᵉⁿ = solvedSTD(prob  = [0.1,0.2,0.7],
                          power = [0.0u"MW",0.0u"MW",2.0u"MW"])
julia> ugfᵍᵉⁿ = UGF(:power, stdᵍᵉⁿ)
julia> isequal(ugfᵍᵉⁿ.val,[0.0u"MW",2.0u"MW"])
true
```
