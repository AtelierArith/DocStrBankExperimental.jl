```
getIndexEnsemble(nvec, bathPtr)
```

Search for all the multi-index ensemble $(\alpha, k)$ where $\alpha$ and $k$ represents the $k$-th exponential-expansion term in the $\alpha$-th bath.

# Parameters

  * `nvec::Nvec` : An object which records the repetition number of each multi-index ensembles in ADOs.
  * `bathPtr::Vector{Tuple{Int, Int}}`: This can be obtained from [`HierarchyDict.bathPtr`](@ref HierarchyDict), [`MixHierarchyDict.bosonPtr`](@ref MixHierarchyDict), or [`MixHierarchyDict.fermionPtr`](@ref MixHierarchyDict).

# Returns

  * `Vector{Tuple{Int, Int, Int}}`: a vector (list) of the tuples $(\alpha, k, n)$.

# Example

Here is an example to use [`Bath`](@ref lib-Bath), [`Exponent`](@ref), [`HierarchyDict`](@ref), and `getIndexEnsemble` together:

```julia
L::M_Fermion;          # suppose this is a fermion type of HEOM Liouvillian superoperator matrix you create
HDict = L.hierarchy;   # the hierarchy dictionary
ados = SteadyState(L); # the stationary state (ADOs) for L 

# Let's consider all the ADOs for first level
idx_list = HDict.lvl2idx[1];

for idx in idx_list
    ρ1 = ados[idx]  # one of the 1st-level ADO
    nvec = HDict.idx2nvec[idx]  # the nvec corresponding to ρ1
    
    for (α, k, n) in getIndexEnsemble(nvec, HDict.bathPtr)
        α  # index of the bath
        k  # the index of the exponential-expansion term in α-th bath
        n  # the repetition number of the ensemble {α, k} in ADOs
        exponent = L.bath[α][k]  # the k-th exponential-expansion term in α-th bath

        # do some calculations you want
    end
end
```
