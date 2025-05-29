```
LSDB([; cost, redundant])
```

Least Statistically Dependent Basis (LSDB). 

# Keyword Arguments

  * `cost::LSDBCost`: (Default: `DifferentialEntropyCost()`) Cost function for LSDB.
  * `redundant::Bool`: (Default: `false`) Whether the performed wavelet transform is redundant. Set `redundant=true` when running LSDB with redundant wavelet transforms such as SWT or ACWT.

**See also:** [`BestBasisType`](@ref), [`JBB`](@ref), [`BB`](@ref)
