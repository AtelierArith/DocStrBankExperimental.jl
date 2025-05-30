[多変量正規分布](http://en.wikipedia.org/wiki/Multivariate_normal_distribution)は、*正規分布*の多次元一般化です。平均ベクトル $\boldsymbol{\mu}$ と共分散行列 $\boldsymbol{\Sigma}$ を持つ d 次元の多変量正規分布の確率密度関数は次のようになります：

$$
f(\mathbf{x}; \boldsymbol{\mu}, \boldsymbol{\Sigma}) = \frac{1}{(2 \pi)^{d/2} |\boldsymbol{\Sigma}|^{1/2}}
\exp \left( - \frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \Sigma^{-1} (\mathbf{x} - \boldsymbol{\mu}) \right)
$$

実際には、平均ベクトルと共分散が特別な形を持つことが多く、これを利用して計算を簡素化することができます。例えば、平均ベクトルは時にはゼロベクトルであることがあり、共分散行列は対角行列であったり、$\sigma^2 \mathbf{I}$ の形であったりします。このような特別なケースを利用するために、平均と共分散の特別な構造を指定できるパラメトリック型 `MvNormal` を以下のように定義します。

```julia
struct MvNormal{T<:Real,Cov<:AbstractPDMat,Mean<:AbstractVector} <: AbstractMvNormal
    μ::Mean
    Σ::Cov
end
```

ここで、平均ベクトルは任意の `AbstractVector` のインスタンスであることができます。共分散は `AbstractPDMat` の任意のサブタイプであることができます。特に、完全共分散には `PDMat`、対角共分散には `PDiagMat`、等方的共分散には $\sigma^2 \mathbf{I}$ の形の `ScalMat` を使用できます。（詳細については、Julia パッケージ [PDMats](https://github.com/JuliaStats/PDMats.jl/) を参照してください）。

また、異なる平均ベクトルと共分散の組み合わせを使用して型のエイリアスのセットを定義します：

```julia
const IsoNormal  = MvNormal{Float64, ScalMat{Float64},                  Vector{Float64}}
const DiagNormal = MvNormal{Float64, PDiagMat{Float64,Vector{Float64}}, Vector{Float64}}
const FullNormal = MvNormal{Float64, PDMat{Float64,Matrix{Float64}},    Vector{Float64}}

const ZeroMeanIsoNormal{Axes}  = MvNormal{Float64, ScalMat{Float64},                  Zeros{Float64,1,Axes}}
const ZeroMeanDiagNormal{Axes} = MvNormal{Float64, PDiagMat{Float64,Vector{Float64}}, Zeros{Float64,1,Axes}}
const ZeroMeanFullNormal{Axes} = MvNormal{Float64, PDMat{Float64,Matrix{Float64}},    Zeros{Float64,1,Axes}}
```

多変量正規分布はアフィン変換をサポートします：

```julia
d = MvNormal(μ, Σ)
c + B * d    # == MvNormal(B * μ + c, B * Σ * B')
dot(b, d)    # == Normal(dot(b, μ), b' * Σ * b)
```
