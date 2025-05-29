等分配列を生成し、可積分関数の値の平均が、nが無限大に近づくにつれて積分に収束する特性を持ちます。

##### 引数

  * `n::Union{Int, Vector{Int}}` : 各次元に沿った望ましいノードの数
  * `a::Union{Real, Vector{Real}}` : 各次元に沿った下端点
  * `b::Union{Real, Vector{Real}}` : 各次元に沿った上端点
  * `kind::AbstractString("N")`: 次のいずれか：

      * N - Neiderreiter（デフォルト）
      * W - Weyl
      * H - Haber
      * R - 擬似乱数

##### 戻り値

  * `nodes::Array{Float64}` : 積分ノードの配列
  * `weights::Array{Float64}` : 対応する積分重みの配列

##### 注意事項

この関数へのパラメータのいずれかがスカラーで、他が長さ `n` のベクトルである場合、スカラーのパラメータは `n` 回繰り返されます。

##### 参考文献

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
