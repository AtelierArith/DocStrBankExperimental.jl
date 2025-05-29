```
SCFconfig{T<:Real, L, MS<:NTuple{L, Val}} <: ImmutableParameter{T, SCFconfig}
```

The `struct` for self-consistent field (SCF) iteration configurations.

≡≡≡ Field(s) ≡≡≡

`method::MS`: The applied convergence methods. They can be specified as the elements inside  an `NTuple{L, Symbol}`, which is then input to the constructor of `SCFconfig` as the  positional argument `methods`. The available configuration(s) corresponding to each method  in terms of keyword arguments are:

| Convergence Method(s)       |                  Configuration(s)                   |               Keyword(s)               |         Range(s)/Option(s)          |          Default(s) |
|:--------------------------- |:---------------------------------------------------:|:--------------------------------------:|:-----------------------------------:| -------------------:|
| `:DD`                       |                  damping strength                   |             `dampStrength`             |             [`0`, `1`]              |               `0.5` |
| `:DIIS`, `:EDIIS`, `:ADIIS` | subspace size; DIIS-Method solver; reset threshold¹ | `DIISsize`; `solver`; `resetThreshold` | `1`,`2`...; `:LBFGS`...; `1e-14`... | `10`; `:LBFGS`; N/A |

¹ The reset threshold (`resetThreshold::Real`) determines when to clear the memory of the  DIIS-based method's subspace and reset the second-to-latest residual vector as the first  reference. The reset is executed when the latest computed energy increases an amount above  the threshold compared to the second-to-latest computed energy. In default, the threshold  is always slightly larger than the machine epsilon of the numerical data type for the SCF  computation.

### Convergence Methods

  * `:DD`: Direct diagonalization of the Fock matrix.
  * `:DIIS`: [Direct inversion in the iterative subspace](https://onlinelibrary.wiley.com/doi/10.1002/jcc.540030413).
  * `:EDIIS`: [Energy-DIIS](https://aip.scitation.org/doi/abs/10.1063/1.1470195).
  * `:ADIIS`: [DIIS based on the augmented Roothaan–Hall (ARH) energy function](https://aip.scitation.org/doi/10.1063/1.3304922).

### DIIS-Method Solvers

  * `:LBFGS`: [Limited-memory BFGS with box constraints](https://github.com/Gnimuc/LBFGSB.jl).
  * `:LCM`: Lagrange multiplier solver.
  * `:SPGB`: [Spectral Projected Gradient Method with box constraints](https://github.com/m3g/SPGBox.jl).

`interval::NTuple{L, T}`: The stopping (or skipping) thresholds for required methods. The  last threshold will be the convergence threshold for the SCF procedure. When the last  threshold is set to `NaN`, there will be no convergence detection.

`methodConfig::NTuple{L, Vector{<:Pair}}`: The additional keywords arguments for each  method stored as `Tuple`s of `Pair`s.

`secondaryConvRatio::NTuple{2, T}`: The ratios of the secondary convergence criteria to the  primary convergence indicator, i.e., the change of the energy (ΔE):

| Order |   Symbols    |                       Meaning                        | Default |
|:----- |:------------:|:----------------------------------------------------:|:-------:|
| 1     | RMS(FDS-SDF) | root mean square of the error matrix defined in DIIS |   50    |
| 2     |   RMS(ΔD)    | root mean square of the change of the density matrix |   50    |

`oscillateThreshold::T`: The threshold for oscillatory convergence.

≡≡≡ Initialization Method(s) ≡≡≡

```
SCFconfig(methods::NTuple{L, Symbol}, intervals::NTuple{L, T}, 
          config::Dict{Int, <:AbstractVector{<:Pair}}=Dict(1=>Pair[]); 
          secondaryConvRatio::Union{Real, NTuple{2, Real}}=(50, 50), 
          oscillateThreshold::Real=1.0e-6) where {L, T} -> 
SCFconfig{T, L}
```

`methods` and `intervals` are the convergence methods to be applied and their stopping  (or skipping) thresholds respectively. `config` specifies additional keyword argument(s)  for each methods by a `Pair` of which the key `i::Int` is for `i`th method and the pointed  `AbstractVector{<:Pair}` is the pairs of keyword arguments and their values respectively.  If `secondaryConvRatio` is `Real`, it will be assigned as the value for all the secondary  convergence ratios.

```
SCFconfig(;threshold::AbstractFloat=(0.001, 1.0e-10), 
           secondaryConvRatio::Union{Real, NTuple{2, Real}}=(50, 50), 
           oscillateThreshold::Real=defaultOscThreshold) -> 
SCFconfig{Float64, 2}
```

`threshold` will update the stopping threshold of the default SCF configuration used in  HFconfig() with a new value. In other words, it updates the stopping threshold of  `:1.0e-10`.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> SCFconfig((:DD, :ADIIS, :DIIS), (1e-4, 1e-12, 1e-13), Dict(2=>[:solver=>:LCM]));

julia> SCFconfig(threshold=1e-8, oscillateThreshold=1e-5)
SCFconfig{Float64, 2, Tuple{Val{:ADIIS}, Val{:DIIS}}}(method, interval=(0.001, 1.0e-8), methodConfig, secondaryConvRatio, oscillateThreshold)
```
