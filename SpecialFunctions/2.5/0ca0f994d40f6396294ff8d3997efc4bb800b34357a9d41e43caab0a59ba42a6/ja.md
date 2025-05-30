```
beta_inc_asymptotic_symmetric(a,b,lambda,epps)
```

$$
I_{x}(a,b)
$$

を漸近展開を用いて計算します。ここで、`a, b >= 15`と仮定します。$\lambda = (a+b)*y - b$と仮定されています。

外部リンク: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

参照: [`beta_inc`](@ref)

# 実装

[Didonato and Morris (1992)](@cite didonato_1992)の`BASYM(A,B,LAMBDA,EPS)`
