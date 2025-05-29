```
runHFcore(HTtype, scfConfig, Ns, Hcore, HeeI, S, X, C0, maxStep, earlyStop, saveTrace, 
          printInfo=false, infoLevel=2) -> 
Tuple{Tuple{Vararg{HFtempVars}}, Bool}
```

Another method of `runHFcore` that has the same return value, but takes more underlying  data as arguments.

=== Positional argument(s) ===

`HTtype::Val{HFT} where HFT`: Hartree–Fock method type. Available values of `HFT` are  :RHF, :UHF.

`scfConfig::SCFconfig`: The SCF iteration configuration.

`Ns::NTuple{HFTS, Int} where HFTS`: The numbers of electrons with same spin configurations. 

`Hcore::AbstractMatrix{T} where T`: The core Hamiltonian of the electronic Hamiltonian.

`HeeI::AbstractArray{T, 4} where T`: The electron-electron interaction tensor (in the  chemists' notation) which includes both the Coulomb interactions and the Exchange  Correlations.

`S::AbstractMatrix{T} where T`: The overlap matrix of the used basis set.

`X::AbstractMatrix{T} where T`: The transformation matrix of `S`.

`C0::NTuple{HFTS, AbstractMatrix{T}} where {HFTS, T}`: Initial guess of the coefficient  matrix(s) of the canonical spin-orbitals.

`maxStep::Int`: Maximum iteration steps allowed regardless if the iteration converges.

`earlyStop::Bool`: Whether automatically terminate (or skip) a convergence method early  when its performance becomes unstable or poor.

`saveTrace::NTuple{4, Bool}`: Determine whether saving (by pushing) the intermediate  information from all the iterations steps to the output [`HFtempVars`](@ref) of  `runHFcore`. Its definition is the same as the field `.saveTrace` inside a  [`HFconfig`](@ref).

`printInfo::Bool`: Whether print out the information of iteration steps and result.

`infoLevel::Int`: Printed info's level of details when `printInfo=true`. The higher  (the absolute value of) it is, more intermediate steps and other information will be  printed. Once `infoLevel` achieve `5`, every step and all available  information will be printed.
