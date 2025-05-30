```
gamma_inc_fsum(a,x)
```

$$
Q(a,x)
$$

を有限和を用いて計算します。条件は`a >= 1 && 2a`が整数であることです。`a <= x <= x0`かつ`a = n/2`のときに使用します。[DiDonato and Morris (1986)](@cite didonato_1986)の論文の式(14)を参照してください。

また、[`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)も参照してください。
