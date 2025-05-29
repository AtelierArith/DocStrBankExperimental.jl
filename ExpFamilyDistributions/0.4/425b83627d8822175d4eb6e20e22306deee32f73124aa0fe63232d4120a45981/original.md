```
mutable struct NormalDiag{T,D} <: ExpFamilyDistribution
    μ
    v
end
```

Normal distribution with a diagonal covariance matrix. `v` is the diagonal of the covariance matrix. Note that you can still access the full covariance matrix by using the property `Σ`.

# Constructors

```
NormalDiag{T,D}()
NormalDiag(μ[, v])
```

where `T` is the encoding type of the parameters, `D` is the dimension of the support, `μ` is a vector and `v` is the diagonal of the covariance matrix.

# Examples

```jldoctest
julia> NormalDiag{Float32, 2}()
NormalDiag{Float32,2}
  μ = Float32[0.0, 0.0]
  v = Float32[1.0, 1.0]

julia> NormalDiag([1.0, 1.0])
NormalDiag{Float64,2}
  μ = [1.0, 1.0]
  v = [1.0, 1.0]

julia> NormalDiag([1.0, 1.0], [2.0, 1.0])
NormalDiag{Float64,2}
  μ = [1.0, 1.0]
  v = [2.0, 1.0]
```
