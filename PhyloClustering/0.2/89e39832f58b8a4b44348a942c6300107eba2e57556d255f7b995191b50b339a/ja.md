```
split_weight(trees::Vector{HybridNetwork}, n::Int64)
```

`Vector{HybridNetwork}`内の系統樹のスプリットウェイト埋め込み。すべての分類群は数字に置き換えられます。数字に対応する分類群の名前を含む辞書を取得するには、関数 [`num_to_name`](@ref) を使用してください。

# 引数

  * `trees`: 木を含むHybridNetworkオブジェクトのベクター
  * `n`: 木の分類群の数

# 出力

バイパーティション形式で木を示す `Matrix{Float64}`

# 例

```jldoctest
julia> split_weight([readTopology("(4:4.249,(1:2.457,(2:2.064,3:2.064):0.393):1.793);"), readTopology("(4:4.308,(2:1.634,(1:1.588,3:1.588):0.046):2.674);")], 4)
2×7 Matrix{Float64}:
 2.457  2.064  2.064  6.042  0.0  0.0    0.393
 1.588  1.634  1.588  6.982  0.0  0.046  0.0
```
