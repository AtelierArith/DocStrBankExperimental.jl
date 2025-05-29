```
struct EigsolveResult
```

A struct containing the eigenvalues, the eigenvectors, and some information from the solver

# Fields (Attributes)

  * `values::AbstractVector`: the eigenvalues
  * `vectors::AbstractMatrix`: the transformation matrix (eigenvectors)
  * `type::Union{Nothing,QuantumObjectType}`: the type of [`QuantumObject`](@ref), or `nothing` means solving eigen equation for general matrix
  * `dimensions::Union{Nothing,AbstractDimensions}`: the `dimensions` of [`QuantumObject`](@ref), or `nothing` means solving eigen equation for general matrix
  * `iter::Int`: the number of iteration during the solving process
  * `numops::Int` : number of times the linear map was applied in krylov methods
  * `converged::Bool`: Whether the result is converged

!!! note "`dims` property"
    For a given `res::EigsolveResult`, `res.dims` or `getproperty(res, :dims)` returns its `dimensions` in the type of integer-vector.


# Examples

One can obtain the eigenvalues and the corresponding [`QuantumObject`](@ref)-type eigenvectors by:

```jldoctest
julia> result = eigenstates(sigmax())
EigsolveResult:   type=Operator()   dims=[2]
values:
2-element Vector{ComplexF64}:
 -1.0 + 0.0im
  1.0 + 0.0im
vectors:
2×2 Matrix{ComplexF64}:
 -0.707107+0.0im  0.707107+0.0im
  0.707107+0.0im  0.707107+0.0im

julia> λ, ψ, U = result;

julia> λ
2-element Vector{ComplexF64}:
 -1.0 + 0.0im
  1.0 + 0.0im

julia> ψ
2-element Vector{QuantumObject{Ket, Dimensions{1, Tuple{Space}}, Vector{ComplexF64}}}:

Quantum Object:   type=Ket()   dims=[2]   size=(2,)
2-element Vector{ComplexF64}:
 -0.7071067811865475 + 0.0im
  0.7071067811865475 + 0.0im

Quantum Object:   type=Ket()   dims=[2]   size=(2,)
2-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im

julia> U
2×2 Matrix{ComplexF64}:
 -0.707107+0.0im  0.707107+0.0im
  0.707107+0.0im  0.707107+0.0im
```
