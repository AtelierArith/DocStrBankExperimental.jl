```
 fdiscond_(sysrf::DescriptorStateSpace, freq) -> (scond, β, γ)
```

Compute for a stable descriptor system `sysrf = (A-λE,B,C,D)` with the transfer function matrix `Rf(λ)`,  `β` - the H∞- index of `Rf(λ)`, `γ` - the maximum of the columns norms of `Rf(λ)` and  `scond` - the column-gains sensitivity condition evaluated as `scond := β/γ`.  If `freq` is a vector of real frequency values, then `β` and `γ` are evaluated over the frequencies contained in `freq`. 
