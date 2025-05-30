```
gamma_inc_asym(a, x, ind)
```

$$
P(a,x)
$$

を次の漸近展開を用いて計算します：

$$
R(a,x)/a * (1 + \sum_{n=1}^{N-1}(a_{n}/x^{n} + \Theta _{n}a_{n}/x^{n}))
$$

ここで`R(a,x) = rgammax(a,x)`です。`1 <= a <= BIG`および`x >= x0`のときに使用されます。

外部リンク: [DLMF 8.11.2](https://dlmf.nist.gov/8.11.2)

参照: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
