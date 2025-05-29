```julia
isplackettburman(d::Matrix{Int64}) -> Bool

```

与えられたデザインがプラケット・バーマンデザインであるかどうかを確認するには、元のプラケット・バーマン論文で得られた以下の特性を確認する必要があります：

1. 各コンポーネントは、その値のそれぞれで同じ回数だけ複製されている、つまり、各列の要素の合計がゼロであること。
2. 各ペアのコンポーネントは、すべての値の組み合わせで同じ回数だけ一緒に出現する、つまり、各ペアの列の合計は、$2$と$-2$の出現回数が同じであり、その数の2倍の$0$の出現回数を持つ列を生成すること。

> Plackett, R.L. and Burman, J.P., 1946. The design of optimum multifactorial experiments. Biometrika, 33(4), pp.305-325.


```jldoctest
julia> isplackettburman(plackettburman(2))
true

julia> isplackettburman(plackettburman(4))
true

julia> isplackettburman(plackettburman(16))
true

julia> isplackettburman(rand(Int, 4,4))
false

```
