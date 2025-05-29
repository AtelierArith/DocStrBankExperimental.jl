多変量一様分布のための数値積分ノードと重みを計算します

##### 引数

  * `n::Union{Int, Vector{Int}}` : 各次元に沿った希望するノードの数
  * `mu::Union{Real, Vector{Real}}` : 各次元に沿った平均
  * `sig2::Union{Real, Vector{Real}, Matrix{Real}}(eye(length(n)))` : 共分散構造

##### 戻り値

  * `nodes::Array{Float64}` : 数値積分ノードの配列
  * `weights::Array{Float64}` : 対応する数値積分重みの配列

##### 注意事項

`qnwnorm`のドキュメントも参照してください

##### 参考文献

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
