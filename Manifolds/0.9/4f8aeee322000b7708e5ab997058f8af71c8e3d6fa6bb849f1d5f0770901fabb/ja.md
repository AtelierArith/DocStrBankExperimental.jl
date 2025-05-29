```
var(M, x, m=mean(M, x); corrected=true)
var(M, x, w::AbstractWeights, m=mean(M, x, w); corrected=false)
```

`M`上の`n`データポイントの`Vector` `x`の（オプションで重み付けされた）分散を計算します。すなわち、

$$
\frac{1}{c} \sum_{i=1}^n w_i d_{\mathcal M}^2 (x_i,m),
$$

ここで`c`は補正項です。詳細は[Statistics.var](https://juliastats.org/StatsBase.jl/stable/scalarstats/#Statistics.var)を参照してください。`x`の平均は`m`として指定でき、補正された分散は`corrected=true`を設定することで有効になります。すべての追加の`kwargs...`は平均の計算に渡されます（提供されていない場合）。
