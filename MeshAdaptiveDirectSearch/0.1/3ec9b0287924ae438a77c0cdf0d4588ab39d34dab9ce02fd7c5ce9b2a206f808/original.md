```
OrthoMADS(N; search = NoSearch(), mesh = LogMesh(), reduction = NegReduction(N))
```

Returns a `MADS` object with `poll = OrthoDirectionGenerator(N)` where `N` is the dimenionality of the problem and `reduction` can be [`NegReduction(N)`](@ref) or [`NoReduction()`](@ref). See Abramson et al. (2009), ORTHOMADS and Audet et al. 2014 for NegReduction.
