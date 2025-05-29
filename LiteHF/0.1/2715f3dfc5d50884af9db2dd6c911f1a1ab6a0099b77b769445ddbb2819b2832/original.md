```
struct ExpCounts{T, M} #M is a long Tuple for unrolling purpose.
    nominal::T
    modifier_names::Vector{Symbol}
    modifiers::M
end
```

A callable struct that returns the expected count given modifier nuisance parameter values. The # of parameters passed must equal to length of `modifiers`. See [_expkernel](@ref)
