```
auxquadgk!(f!, result, a,b,c...; rtol=sqrt(eps), atol=0, maxevals=10^7, order=7, norm=norm)
```

[`auxquadgk`](@ref)と同様ですが、配列値の被積分関数（またはインプレース操作をサポートする他の可変型）に対してインプレース操作を利用します。特に、`quadgk`との違いは2つあります：

1. 関数`f!`は`f!(y, x) = y .= f(x)`の形である必要があります。つまり、被積分関数`f(x)`の戻り値を最初の引数`y`にインプレースで書き込みます。（`f!`の戻り値は無視されます。）
2. `auxquadgk`と同様に、戻り値は推定された積分値`I`と推定された誤差`E`のタプル`(I,E)`です。しかし、`auxquadgk!`では推定された積分値が`result`引数にインプレースで書き込まれるため、`I === result`となります。

それ以外は、`auxquadgk`と同じ動作です。

コンパイル時に長さが知られている*小さな*配列の値を持つ被積分関数に対しては、通常、`quadgk`を使用し、被積分関数を[StaticArrays.jlパッケージ](https://github.com/JuliaArrays/StaticArrays.jl)から`SVector`を返すように変更する方が効率的です。
