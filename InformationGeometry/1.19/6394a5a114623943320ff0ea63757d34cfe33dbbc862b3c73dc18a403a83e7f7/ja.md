```
OrthVF(DM::DataModel, PL::Plane, θ::AbstractVector{<:Number}; ADmode::Val=Val(:ForwardDiff)) -> Vector
```

パラメータ構成 $\theta$ に対して、対数尤度の値が変化しない方向（パラメータ空間内）を計算します。2D `Plane` が指定されているため、入力 `θ` と出力の両方に2つのコンポーネントがあります。`ADmode=Val(false)` は、`DM` に提供された `model` とヤコビアン `dmodel` を別々に評価することによってスコアを計算します。`ADmode` の他の選択肢は、対数尤度の式を微分することによってスコアを直接計算し、すなわちデュアル変数に対して1回の評価のみが行われます。
