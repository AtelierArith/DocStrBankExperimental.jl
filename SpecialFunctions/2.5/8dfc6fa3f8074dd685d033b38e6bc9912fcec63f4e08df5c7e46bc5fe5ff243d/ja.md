```
gamma_inc_taylor_x(a,x,ind)
```

$$
P(a,x)
$$

を次のようにテイラー展開に基づいて計算します：

$$
J = -a * \sum_{1}^{\infty} (-x)^{n}/((a+n)n!)
$$

また、$P(a,x)/x^a$は次のように与えられます：

$$
(1 - J) / \Gamma(a+1)
$$

これは`gamma_inc(a,x,ind)`の項ごとの積分から得られます。これは`a < 1`かつ`x < 1.1`のときに使用されます - [DiDonato & Morris (1986)](@cite didonato_1986)のEqn (9)を参照してください。

関連情報：[`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
