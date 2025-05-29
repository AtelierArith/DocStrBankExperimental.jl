The [Multivariate normal distribution](http://en.wikipedia.org/wiki/Multivariate_normal_distribution) is a multidimensional generalization of the *normal distribution*. The probability density function of a d-dimensional multivariate normal distribution with mean vector $\boldsymbol{\mu}$ and covariance matrix $\boldsymbol{\Sigma}$ is:

$$
f(\mathbf{x}; \boldsymbol{\mu}, \boldsymbol{\Sigma}) = \frac{1}{(2 \pi)^{d/2} |\boldsymbol{\Sigma}|^{1/2}}
\exp \left( - \frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \Sigma^{-1} (\mathbf{x} - \boldsymbol{\mu}) \right)
$$

We realize that the mean vector and the covariance often have special forms in practice, which can be exploited to simplify the computation. For example, the mean vector is sometimes just a zero vector, while the covariance matrix can be a diagonal matrix or even in the form of $\sigma^2 \mathbf{I}$. To take advantage of such special cases, we introduce a parametric type `MvNormal`, defined as below, which allows users to specify the special structure of the mean and covariance.

```julia
struct MvNormal{T<:Real,Cov<:AbstractPDMat,Mean<:AbstractVector} <: AbstractMvNormal
    μ::Mean
    Σ::Cov
end
```

Here, the mean vector can be an instance of any `AbstractVector`. The covariance can be of any subtype of `AbstractPDMat`. Particularly, one can use `PDMat` for full covariance, `PDiagMat` for diagonal covariance, and `ScalMat` for the isotropic covariance – those in the form of $\sigma^2 \mathbf{I}$. (See the Julia package [PDMats](https://github.com/JuliaStats/PDMats.jl/) for details).

We also define a set of aliases for the types using different combinations of mean vectors and covariance:

```julia
const IsoNormal  = MvNormal{Float64, ScalMat{Float64},                  Vector{Float64}}
const DiagNormal = MvNormal{Float64, PDiagMat{Float64,Vector{Float64}}, Vector{Float64}}
const FullNormal = MvNormal{Float64, PDMat{Float64,Matrix{Float64}},    Vector{Float64}}

const ZeroMeanIsoNormal{Axes}  = MvNormal{Float64, ScalMat{Float64},                  Zeros{Float64,1,Axes}}
const ZeroMeanDiagNormal{Axes} = MvNormal{Float64, PDiagMat{Float64,Vector{Float64}}, Zeros{Float64,1,Axes}}
const ZeroMeanFullNormal{Axes} = MvNormal{Float64, PDMat{Float64,Matrix{Float64}},    Zeros{Float64,1,Axes}}
```

Multivariate normal distributions support affine transformations:

```julia
d = MvNormal(μ, Σ)
c + B * d    # == MvNormal(B * μ + c, B * Σ * B')
dot(b, d)    # == Normal(dot(b, μ), b' * Σ * b)
```
