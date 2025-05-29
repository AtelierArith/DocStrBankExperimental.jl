```
rm_hermite(N::Int,mu::Real)
rm_hermite(N::Int)
```

$$
(-\infty,\infty)
$$

上で$w(t) = |t|^{2 \mu} \mathrm{e}^{-t^2}$に対して直交する単項一般化エルミート多項式のための$N$再帰係数を作成します。

呼び出し`rm_hermite(N)`は`rm_hermite(N,0)`と同じです。
