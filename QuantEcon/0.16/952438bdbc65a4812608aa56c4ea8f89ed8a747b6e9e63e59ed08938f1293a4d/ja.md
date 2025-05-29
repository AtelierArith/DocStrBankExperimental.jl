多変量台形法の数値積分ノードと重みを計算します。

##### 引数

  * `n::Union{Int, Vector{Int}}` : 各次元に沿った希望するノードの数
  * `a::Union{Real, Vector{Real}}` : 各次元に沿った下端点
  * `b::Union{Real, Vector{Real}}` : 各次元に沿った上端点

##### 戻り値

  * `nodes::Array{Float64}` : 数値積分ノードの配列
  * `weights::Array{Float64}` : 対応する数値積分重みの配列

##### 注意事項

この関数へのパラメータのいずれかがスカラーで、他が長さ `n` のベクトルである場合、スカラーのパラメータは `n` 回繰り返されます。

##### 参考文献

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
