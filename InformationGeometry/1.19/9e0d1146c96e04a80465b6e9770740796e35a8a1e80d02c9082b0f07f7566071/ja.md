```
Score(DM::DataModel, θ::AbstractVector{<:Number}; ADmode::Val=Val(:ForwardDiff))
```

パラメータ $\theta$ に関する対数尤度 $\ell$ の勾配を計算します。`ADmode=Val(false)` は、`DM` に提供されたヤコビアン `dmodel` を使用してスコアを計算します。つまり、`model` と `dmodel` の両方を別々に評価する必要があります。他の `ADmode` の選択肢は、対数尤度の式を微分することによってスコアを直接計算します。つまり、双対変数に対して1回の評価のみが行われます。
