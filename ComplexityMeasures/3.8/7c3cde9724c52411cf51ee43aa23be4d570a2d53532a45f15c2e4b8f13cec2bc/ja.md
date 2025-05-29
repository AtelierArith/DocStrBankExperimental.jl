```
entropy_distribution(x; τ = 1, m = 3, n = 3, base = 2)
```

`x`の分布エントロピーを[Li2015](@cite)を使用して、遅延/ラグ`τ`を持つ埋め込み次元`m`で計算し、距離の分布に対する確率を推定するために`n`要素の等間隔ビニングを使用し、チェビシェフ距離メトリックを使用します。

この関数は単なる便利な呼び出しです：

```julia
x = rand(1000000)
o = SequentialPairDistances(x, n, m, τ, metric = Chebyshev())
h = information(Shannon(base = 2), o, x)
```

詳細については[`SequentialPairDistances`](@ref)を参照してください。
