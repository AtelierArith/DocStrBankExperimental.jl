```
ReducedDensityMatrix{T=Float64}(p) <: AbstractObservable{Hermitian{T, Matrix{T}}}
```

A matrix-valued operator that can be used to calculate the `p`-particle reduced density matrix. The matrix elements are defined as:

$$
\hat{ρ}^{(p)}_{j_1,...,j_1,k_1,...,k_p} =  \prod_{i=1}^{p} â^†_{j_i} \prod_{l=p}^{1} â_{k_{l}}
$$

The integer indices `j_i` and `k_i` represent single particle modes. For efficiency they are chosen to be distinct and ordered:

$$
j_1 < j_2 < \ldots < j_{p} \quad \land \quad k_1 < k_2 < \ldots < k_{p}
$$

`ReducedDensityMatrix` can be used to construct the single-particle reduced density matrix (with `p == 1`) for fermionic and bosonic Fock spaces with address types [`<: SingleComponentFockAddress`](@ref SingleComponentFockAddress). For higher order reduced density matrices with `p > 1` only fermionic Fock addresses ([`FermiFS`](@ref)) are supported due to the ordering of indices.

`ReducedDensityMatrix` can be used with [`dot`](@ref) or [`AllOverlaps`](@ref) to calculate the whole matrix in one go.

# Examples

```jldoctest
julia> dvec_b = PDVec(BoseFS(1,1) => 0.5, BoseFS(2,0) => 0.5)
2-element PDVec: style = IsDeterministic{Float64}()
  fs"|2 0⟩" => 0.5
  fs"|1 1⟩" => 0.5

julia> Op1 = ReducedDensityMatrix(1)
ReducedDensityMatrix{Float64}(1)

julia> dot(dvec_b, Op1, dvec_b)
2×2 Hermitian{Float64, Matrix{Float64}}:
 0.75      0.353553
 0.353553  0.25

julia> Op2 = ReducedDensityMatrix{Float32}(2)
ReducedDensityMatrix{Float32}(2)

julia> dot(dvec_b, Op2, dvec_b)
ERROR: ArgumentError: ReducedDensityMatrix(p) with `p > 1` requires `FermiFS` addresses

julia> dvec_f = PDVec(FermiFS(1,1,0,0) => 0.5, FermiFS(0,1,1,0) => 0.5)
2-element PDVec: style = IsDeterministic{Float64}()
  fs"|⋅↑↑⋅⟩" => 0.5
  fs"|↑↑⋅⋅⟩" => 0.5

julia> dot(dvec_f, Op2, dvec_f)
6×6 Hermitian{Float32, Matrix{Float32}}:
 0.25  0.0  0.25  0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
 0.25  0.0  0.25  0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
```

See also [`single_particle_density`](@ref), [`SingleParticleDensity`](@ref), [`SingleParticleExcitation`](@ref), [`TwoParticleExcitation`](@ref).
