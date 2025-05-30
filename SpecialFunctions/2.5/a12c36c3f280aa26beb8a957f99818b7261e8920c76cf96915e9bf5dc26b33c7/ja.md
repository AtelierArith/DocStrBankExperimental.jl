```
beta_inc_cont_fraction(a,b,x,y,lambda,epps)
```

$$
I_{x}(a,b)
$$

を連分数展開を用いて計算します。ただし、`a, b > 1`とします。$\lambda = (a+b)*y - b$と仮定します。

外部リンク: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

参照: [`beta_inc`](@ref)

# 実装

[Didonato and Morris (1992)](@cite didonato_1992) の`BFRAC(A,B,X,Y,LAMBDA,EPS)`
