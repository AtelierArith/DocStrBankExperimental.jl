```
overapproximate(vTM::Vector{TaylorModelN{N, T, S}}, ::Type{<:Zonotope};
                [remove_redundant_generators]::Bool=true
                [normalize]::Bool=true) where {N, T, S}
```

Overapproximate a multivariate Taylor model with a zonotope.

### Input

  * `vTM`       – vector of `TaylorModelN`
  * `Zonotope`  – target set type
  * `remove_redundant_generators` – (optional; default: `true`) flag to remove                                  redundant generators of the resulting zonotope
  * `normalize` – (optional; default: `true`) flag to skip the normalization of                the Taylor models

### Output

A zonotope that overapproximates the range of the given Taylor model.

### Examples

Consider a vector of two 2-dimensional Taylor models of order 2 and 4, respectively.

```jldoctest
julia> using LazySets, TaylorModels

julia> const IA = IntervalArithmetic;

julia> x₁, x₂ = set_variables(Float64, ["x₁", "x₂"], order=8)
2-element Vector{TaylorN{Float64}}:
  1.0 x₁ + 𝒪(‖x‖⁹)
  1.0 x₂ + 𝒪(‖x‖⁹)

julia> x₀ = IA.IntervalBox(0..0, 2) # expansion point
[0, 0]²

julia> Dx₁ = IA.interval(0.0, 3.0) # domain for x₁
[0, 3]

julia> Dx₂ = IA.interval(-1.0, 1.0) # domain for x₂
[-1, 1]

julia> D = Dx₁ × Dx₂ # take the Cartesian product of the domain on each variable
[0, 3] × [-1, 1]

julia> r = IA.interval(-0.5, 0.5) # interval remainder
[-0.5, 0.5]

julia> p1 = 1 + x₁^2 - x₂
 1.0 - 1.0 x₂ + 1.0 x₁² + 𝒪(‖x‖⁹)

julia> p2 = x₂^3 + 3x₁^4 + x₁ + 1
 1.0 + 1.0 x₁ + 1.0 x₂³ + 3.0 x₁⁴ + 𝒪(‖x‖⁹)

julia> vTM = [TaylorModelN(pi, r, x₀, D) for pi in [p1, p2]]
2-element Vector{TaylorModelN{2, Float64, Float64}}:
            1.0 - 1.0 x₂ + 1.0 x₁² + [-0.5, 0.5]
  1.0 + 1.0 x₁ + 1.0 x₂³ + 3.0 x₁⁴ + [-0.5, 0.5]

julia> Z = overapproximate(vTM, Zonotope);

julia> center(Z)
2-element Vector{Float64}:
   5.5
 124.0

julia> Matrix(genmat(Z))
2×2 Matrix{Float64}:
   0.0  -6.0
 124.5   0.0
```

### Algorithm

We refer to the algorithm description for the univariate case.
