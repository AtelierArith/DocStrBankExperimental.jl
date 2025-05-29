```
OrthVF(DM::DataModel, θ::AbstractVector{<:Number}; ADmode::Val=Val(:ForwardDiff)) -> Vector
```

パラメータ設定 $\theta$ に対して、対数尤度の値が変化しない方向（パラメータ空間内）を計算します。`ADmode=Val(false)` は、`model` と `DM` に提供されたヤコビアン `dmodel` を別々に評価することによってスコアを計算します。`ADmode` の他の選択肢は、対数尤度の式を微分することによってスコアを直接計算し、すなわちデュアル変数に対して1回の評価のみが行われます。
