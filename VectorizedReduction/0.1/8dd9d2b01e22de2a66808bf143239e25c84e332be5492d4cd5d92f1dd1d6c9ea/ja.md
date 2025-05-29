```
vmapreducethen(f, op, g, A::AbstractArray; dims=:, init)
```

関数 `f` を配列 `A` の各要素に適用し、結果を次元 `dims` に沿って二項関数 `op` で減算し、その後結果に `g` を適用します。これは `g.(mapreduce(f, op, A, dims=dims, init=init))` と同等ですが、前述の式によって暗黙的に生成される中間結果を回避し、後処理の変換 `g` を融合させることで出力配列が一度のパスで生成されるようにします。

減算には初期値 `init` が必要で、これは `<:Number` であるか、単一の型引数を受け取る関数（例: `zero`）である必要があります。`init` は二項演算子 `+`、`*`、`min`、および `max` に対してはオプションです。

# 例

```jldoctest
julia> vmapreducethen(abs2, +, √, [1 2; 3 4], dims=1)    # L₂ノルム; `vnorm` を参照
1×2 Matrix{Float64}:
 3.16228  4.47214

julia> vmapreducethen(abs2, +, √, [1 2; 3 4], dims=2, init=1000.0)
2×1 Matrix{Float64}:
 31.701734968294716
 32.01562118716424

julia> vmapreducethen(exp, +, log, [5 6; 7 8], dims=1)    # LSE、ただし `vlogsumexp` を推奨
1×2 Matrix{Float64}:
 7.12693  8.12693
```
