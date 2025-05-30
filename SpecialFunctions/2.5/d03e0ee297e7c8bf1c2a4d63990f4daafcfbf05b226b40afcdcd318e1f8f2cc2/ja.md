```
beta_inc_power_series(a, b, x, epps)
```

$$
I_x(a,b)
$$

を冪級数を用いて計算します：

$$
I_{x}(a,b) = G(a,b) x^{a}/a \left[1 + a \sum_{j=1}^{\infty} ((1-b)(2-b)\dots(j-b)/j!(a+j)) x^{j}\right]
$$

外部リンク: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

参照: [`beta_inc`](@ref)

# 実装

[Didonato and Morris (1992)](@cite didonato_1992) の `BPSER(A,B,X,EPS)`
