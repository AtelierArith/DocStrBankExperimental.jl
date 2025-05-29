```
puredephasingmpo(ΔE, dchain, Nchain, chainparams; tree=false)
```

Generate MPO for a pure dephasing model, defined by the Hamiltonian $H = \frac{ΔE}{2} σ_z +  \frac{σ_z}{2} c_0 (b_0^\dagger + b_0) + \sum_{i=0}^{N-1} t_i (b_{i+1}^\dagger b_i +h.c.) + \sum_{i=0}^{N-1} ϵ_i b_i^\dagger b_i$

The spin is on site 1 of the MPS and the bath modes are to the right.

### Arguments

  * `ΔE::Real`: energy splitting of the spin
  * `dchain::Int`: physical dimension of the chain sites truncated Hilbert spaces
  * `Nchain::Int`: number of sites in the chain
  * `chainparams::Array{Real,1}`: chain parameters for the bath chain. The chain parameters are given in the standard form: `chainparams` $=[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$.
  * `tree::Bool`: if true, return a `TreeNetwork` object, otherwise return a vector of MPO tensors
