```
MvNormalCanon
```

多変量正規分布は[指数族分布](http://en.wikipedia.org/wiki/Exponential_family)であり、2つの*標準パラメータ*を持ちます：*ポテンシャルベクトル* $\mathbf{h}$ と *精度行列* $\mathbf{J}$。これらのパラメータと従来の表現（*すなわち* 平均 $\boldsymbol{\mu}$ と共分散 $\boldsymbol{\Sigma}$ を使用するもの）との関係は次の通りです：

$$
\mathbf{h} = \boldsymbol{\Sigma}^{-1} \boldsymbol{\mu}, \quad \text{ および } \quad \mathbf{J} = \boldsymbol{\Sigma}^{-1}
$$

標準パラメータ化はベイズ分析で広く使用されています。私たちは、標準パラメータを使用して多変量正規分布を表現するための型 `MvNormalCanon` を提供します。特に、`MvNormalCanon` は次のように定義されています：

```julia
struct MvNormalCanon{T<:Real,P<:AbstractPDMat,V<:AbstractVector} <: AbstractMvNormal
    μ::V    # 平均ベクトル
    h::V    # ポテンシャルベクトル、すなわち inv(Σ) * μ
    J::P    # 精度行列、すなわち inv(Σ)
end
```

このパラメトリック型の一般的な特殊化のためのエイリアスも定義します：

```julia
const FullNormalCanon = MvNormalCanon{Float64, PDMat{Float64,Matrix{Float64}},    Vector{Float64}}
const DiagNormalCanon = MvNormalCanon{Float64, PDiagMat{Float64,Vector{Float64}}, Vector{Float64}}
const IsoNormalCanon  = MvNormalCanon{Float64, ScalMat{Float64},                  Vector{Float64}}

const ZeroMeanFullNormalCanon{Axes} = MvNormalCanon{Float64, PDMat{Float64,Matrix{Float64}},    Zeros{Float64,1,Axes}}
const ZeroMeanDiagNormalCanon{Axes} = MvNormalCanon{Float64, PDiagMat{Float64,Vector{Float64}}, Zeros{Float64,1,Axes}}
const ZeroMeanIsoNormalCanon{Axes}  = MvNormalCanon{Float64, ScalMat{Float64},                  Zeros{Float64,1,Axes}}
```

**注意:** `MvNormalCanon` は `MvNormal` と同じメソッドのセットを共有します。
