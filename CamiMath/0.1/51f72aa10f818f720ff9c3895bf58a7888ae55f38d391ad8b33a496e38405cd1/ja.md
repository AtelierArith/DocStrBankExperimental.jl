```
laguerre_polynom(n::Integer [; msg=true])
```

[`laguerreL`](@ref) の係数は次数 `n` のため、

$$
    v(n)=[c_0, c_1, \cdots\ c_n],
$$

ここで

$$
    c_k(n) = \frac{\Gamma(n+1)}{\Gamma(k+1)}\frac{(-1)^{k}}{(n-k)!}\frac{1}{k!}
$$

$$
k=0,1,⋯,n
$$

のとき。

  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

#### 例:

```
julia> laguerre_polynom(7)
(1//1, -7//1, 21//2, -35//6, 35//24, -7//40, 7//720, -1//5040)
```
