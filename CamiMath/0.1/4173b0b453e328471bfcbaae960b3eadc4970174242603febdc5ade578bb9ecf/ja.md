```
hermite_polynom(n::Integer [; msg=true])
```

[`hermiteH`](@ref) の次数 `n` に対する係数は、

$$
    v(n)=[c_0, c_1, \cdots\ c_n],
$$

ここで

$$
    c_k(n) = (-1)^{m}\frac{n!}{k!}\frac{2^{k}}{m!}
$$

$ m = (n-k)/2 $ および $ k=0,1,⋯,n $ です。

  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

#### 例:

```
julia> hermite_polynom(7)
(0, -1680, 0, 3360, 0, -1344, 0, 128)
```
