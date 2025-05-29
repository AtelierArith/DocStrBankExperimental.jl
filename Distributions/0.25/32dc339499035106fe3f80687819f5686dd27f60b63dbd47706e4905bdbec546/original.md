```
MvNormalCanon
```

The multivariate normal distribution is an [exponential family distribution](http://en.wikipedia.org/wiki/Exponential_family), with two *canonical parameters*: the *potential vector* $\mathbf{h}$ and the *precision matrix* $\mathbf{J}$. The relation between these parameters and the conventional representation (*i.e.* the one using mean $\boldsymbol{\mu}$ and covariance $\boldsymbol{\Sigma}$) is:

$$
\mathbf{h} = \boldsymbol{\Sigma}^{-1} \boldsymbol{\mu}, \quad \text{ and } \quad \mathbf{J} = \boldsymbol{\Sigma}^{-1}
$$

The canonical parameterization is widely used in Bayesian analysis. We provide a type `MvNormalCanon`, which is also a subtype of `AbstractMvNormal` to represent a multivariate normal distribution using canonical parameters. Particularly, `MvNormalCanon` is defined as:

```julia
struct MvNormalCanon{T<:Real,P<:AbstractPDMat,V<:AbstractVector} <: AbstractMvNormal
    μ::V    # the mean vector
    h::V    # potential vector, i.e. inv(Σ) * μ
    J::P    # precision matrix, i.e. inv(Σ)
end
```

We also define aliases for common specializations of this parametric type:

```julia
const FullNormalCanon = MvNormalCanon{Float64, PDMat{Float64,Matrix{Float64}},    Vector{Float64}}
const DiagNormalCanon = MvNormalCanon{Float64, PDiagMat{Float64,Vector{Float64}}, Vector{Float64}}
const IsoNormalCanon  = MvNormalCanon{Float64, ScalMat{Float64},                  Vector{Float64}}

const ZeroMeanFullNormalCanon{Axes} = MvNormalCanon{Float64, PDMat{Float64,Matrix{Float64}},    Zeros{Float64,1,Axes}}
const ZeroMeanDiagNormalCanon{Axes} = MvNormalCanon{Float64, PDiagMat{Float64,Vector{Float64}}, Zeros{Float64,1,Axes}}
const ZeroMeanIsoNormalCanon{Axes}  = MvNormalCanon{Float64, ScalMat{Float64},                  Zeros{Float64,1,Axes}}
```

**Note:** `MvNormalCanon` share the same set of methods as `MvNormal`.
