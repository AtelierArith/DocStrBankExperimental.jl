ベータ分布のノードと重みを計算します

##### 引数

  * `n::Union{Int, Vector{Int}}` : 各次元に沿った希望するノードの数
  * `a::Union{Real, Vector{Real}}` : 各次元に沿ったガンマ分布の形状パラメータ。正でなければなりません。デフォルトは1
  * `b::Union{Real, Vector{Real}}` : 各次元に沿ったガンマ分布のスケールパラメータ。正でなければなりません。デフォルトは1

##### 戻り値

  * `nodes::Array{Float64}` : 量子化ノードの配列
  * `weights::Array{Float64}` : 対応する量子化重みの配列

##### 注意事項

この関数へのパラメータのいずれかがスカラーで、他が長さ `n` のベクトルである場合、スカラーのパラメータは `n` 回繰り返されます。

##### 参考文献

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
