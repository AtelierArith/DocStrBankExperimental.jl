```
mutable struct GMTcpt
```

この構造体のフィールドは次のとおりです：

  * `colormap::Array{Float64,2}`:  cptの最初の3列に等しいMx3行列
  * `alpha::Array{Float64,1}`:     各色に対するアルファ値のベクトル
  * `range::Array{Float64,2}`:     各スライスのz範囲を持つMx2行列
  * `minmax::Array{Float64,1}`:    zmin,zmaxを持つ2要素のベクトル
  * `bfn::Array{Float64,2}`:       [0 1]の範囲でのBFN色を持つ3x3(4?)行列（行ごとに1色）
  * `depth::Cint`:                 色深度：24、8、1
  * `hinge::Cdouble`:              不連続な色のブレークでのZ値、またはNaN
  * `cpt::Array{Float64,2}`:       各スライスのz1 z2に対するr1 g1 b1 r2 g2 b2を持つMx6行列
  * `egorical::Int`:               このCPTはカテゴリカルですか？ 0 = いいえ、1 = はい、2 = はい、キーは文字列です。
  * `label::Vector{String}`:       カテゴリカルCPTのラベル
  * `key::Vector{String}`:         カテゴリカルCPTのキー
  * `model::String`:               rgb、hsv、またはcmykの色モデルを持つ文字列 [rgb]
  * `comment::Vector{String}`:     コメントを持つセル配列
