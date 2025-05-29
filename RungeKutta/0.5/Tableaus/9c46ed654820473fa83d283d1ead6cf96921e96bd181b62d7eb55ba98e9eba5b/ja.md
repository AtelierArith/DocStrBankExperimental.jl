Lobatto IIIG テーブルの s ステージ

```julia
TableauLobattoIIIG(::Type{T}, s)
TableauLobattoIIIG(s) = TableauLobattoIIIG(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素型 `T` を受け取ります。

[`TableauLobattoIIIF`](@ref) のためのシンプレクティック化アルゴリズム

係数は $a^G = \frac{1}{2} ( a^F + \bar{a}^F )$ として取られ、係数 $\bar{a}^F$ は、シンプレクティック条件 $b_{i} \bar{a}_{i,j} + \bar{b}_{j} a_{j,i} = b_{i} \bar{b}_{j}$ および $b_{i} = \bar{b}_i$ がすべての $1 \le i,j \le s$ に対して成り立つように計算されます。
