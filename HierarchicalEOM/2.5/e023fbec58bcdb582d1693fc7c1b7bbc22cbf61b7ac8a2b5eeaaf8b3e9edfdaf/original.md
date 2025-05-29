```
M_Boson_Fermion(Hsys, Btier, Ftier, Bbath, Fbath, parity=EVEN; threshold=0.0, verbose=true)
```

Generate the boson-fermion-type HEOM Liouvillian superoperator matrix

# Parameters

  * `Hsys` : The time-independent system Hamiltonian or Liouvillian
  * `Btier::Int` : the tier (cutoff level) for the bosonic bath
  * `Ftier::Int` : the tier (cutoff level) for the fermionic bath
  * `Bbath::Vector{BosonBath}` : objects for different bosonic baths
  * `Fbath::Vector{FermionBath}` : objects for different fermionic baths
  * `parity::AbstractParity` : the parity label of the operator which HEOMLS is acting on (usually `EVEN`, only set as `ODD` for calculating spectrum of fermionic system).
  * `threshold::Real` : The threshold of the importance value (see Ref. [1, 2]). Defaults to `0.0`.
  * `verbose::Bool` : To display verbose output and progress bar during the process or not. Defaults to `true`.

Note that the parity only need to be set as `ODD` when the system contains fermion systems and you need to calculate the spectrum of it.

[1] [Phys. Rev. B  88, 235426 (2013)](https://doi.org/10.1103/PhysRevB.88.235426) [2] [Phys. Rev. B 103, 235413 (2021)](https://doi.org/10.1103/PhysRevB.103.235413)
