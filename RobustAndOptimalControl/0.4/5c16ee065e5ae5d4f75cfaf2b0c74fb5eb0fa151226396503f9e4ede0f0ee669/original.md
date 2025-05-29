```
sim_diskmargin(P::LTISystem, C::LTISystem, σ::Real = 0)
```

Simultaneuous diskmargin at both outputs and inputs of `P`. Ref: "An Introduction to Disk Margins", Peter Seiler, Andrew Packard, and Pascal Gahinet https://arxiv.org/abs/2003.04771 See also [`ncfmargin`](@ref).
