```
PNSystem{ST, PNOrder}
```

Base type for all PN systems, such as `BBH`, `BHNS`, and `NSNS`.

These objects encode all essential properties of the binary, including its current state. As such, they can be used as inputs to the various [fundamental](@ref Fundamental-variables) and [derived variables](@ref Derived-variables), as well as [PN expressions](@ref) and [dynamics](@ref Dynamics) functions.

All subtypes should contain a `state` vector holding all of the fundamental variables for the given type of system.  The parameter `ST` is the type of the `state` vector — for example, `Vector{Float64}`.  `PNOrder` is a `Rational` giving the order to which PN expansions should be carried.
