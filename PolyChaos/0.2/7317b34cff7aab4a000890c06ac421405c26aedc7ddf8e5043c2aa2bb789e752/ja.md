```
rm_laguerre(N::Int,a::Real)
rm_laguerre(N::Int)
```

$$
w(t) = t^a \mathrm{e}^{-t}
$$

に対して$(0,\infty)$上で直交する単項一般化ラグランジュ多項式のための$N$再帰係数を作成します。

呼び出し`rm_laguerre(N)`は`rm_laguerre(N,0)`と同じです。
