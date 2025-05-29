```
JBB([; cost, redundant])
```

Joint Best Basis (JBB).

# Keyword Arguments

  * `cost::JBBCost`: (Default: `LoglpCost(2)`) Cost function for JBB.
  * `redundant::Bool`: (Default: `false`) Whether the performed wavelet transform is redundant. Set `redundant=true` when running LSDB with redundant wavelet transforms such as SWT or ACWT.

**See also:** [`BestBasisType`](@ref), [`LSDB`](@ref), [`BB`](@ref)
