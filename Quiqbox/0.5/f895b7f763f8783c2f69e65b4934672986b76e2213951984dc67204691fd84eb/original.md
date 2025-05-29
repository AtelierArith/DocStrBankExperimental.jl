```
HFconfig{T1, HFT, F, T2, L, MS} <: ConfigBox{T1, HFconfig, HFT}
```

The container of Hartree–Fock method configuration.

≡≡≡ Field(s) ≡≡≡

`HF::Val{HFT}`: Hartree–Fock method type. Available values of `HFT` are  :RHF, :UHF.

`C0::InitialC{T1, HFT, F}`: Initial guess of the orbital coefficient matrix(s) C of the  canonical orbitals. When `C0` is as an argument of `HFconfig`'s constructor, it can be set  to `sym::Symbol` where available values of `sym` are  `:GWH, :Hcore, :SAD`; it can also be a `Tuple` of  prepared orbital coefficient matrix(s) for the corresponding Hartree–Fock method type.

`SCF::SCFconfig{T2, L, MS}`: SCF iteration configuration. For more information please refer  to [`SCFconfig`](@ref).

`maxStep::Int`: Maximum iteration steps allowed regardless if the iteration converges.

`earlyStop::Bool`: Whether automatically terminate (or skip) a convergence method early  when its performance becomes unstable or poor.

`saveTrace::NTuple{4, Bool}`: Determine whether saving (by pushing) the intermediate  information from all the iterations steps to the field `.temp` of the output  [`HFfinalVars`](@ref) of `runHF`. The types of relevant information are:

| Sequence |            Information             | Corresponding field in [`HFtempVars`](@ref) |
|:--------:|:----------------------------------:|:-------------------------------------------:|
|    1     |   orbital coefficient matrix(s)    |                    `.Cs`                    |
|    2     |         density matrix(s)          |           `.Ds`, `.shared.Dtots`            |
|    3     |           Fock matrix(s)           |                    `.Fs`                    |
|    4     | unconverged Hartree–Fock energy(s) |           `.Es`, `.shared.Etots`            |

≡≡≡ Initialization Method(s) ≡≡≡

```
HFconfig(;HF::Union{Symbol, Val}=:RHF, 
          C0::Union{Tuple{AbstractMatrix}, NTuple{2, AbstractMatrix}, 
                    Symbol, Val}=:SAD, 
          SCF::SCFconfig=Quiqbox.SCFconfig{Float64, 2, Tuple{Val{:ADIIS}, Val{:DIIS}}}(method, interval=(0.001, 1.0e-10), methodConfig, secondaryConvRatio, oscillateThreshold), 
          maxStep::Int=150, 
          earlyStop::Bool=true, 
          saveTrace::NTuple{4, Bool}=(false, false, false, true)) -> 
HFconfig
```

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> HFconfig();

julia> HFconfig(HF=:UHF);
```
