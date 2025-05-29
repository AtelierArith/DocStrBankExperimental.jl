```
BB([; cost, redundant])
```

Standard Best Basis (BB). 

# Keyword Arguments

  * `cost::BBCost`: (Default: `ShannonEntropyCost()`) Cost function for BB.
  * `redundant::Bool`: (Default: `false`) Whether the performed wavelet transform is redundant. Set `redundant=true` when running LSDB with redundant wavelet transforms such as SWT or ACWT.

**See also:** [`BestBasisType`](@ref), [`LSDB`](@ref), [`JBB`](@ref)
