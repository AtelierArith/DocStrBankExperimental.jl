```
T = correlation(dualpsi,psi,inputoperators...[,sites=ntuple(i->1,length(inputoperators)),trail=()])
```

Computes the general correlation on the input MPS `psi` with operators defined in the tuple `inputoperators`. The `sites` command specifies which sites to allow for the operators to be applied (i.e., some operators can skip some sites) and the `trail` option allows for a trailing operator like the Fermion sign operator; output is a tensor `T` of rank equal to the size of `inputoperators`

See also: [`expect`](@ref) [`correlationmatrix`](@ref)
