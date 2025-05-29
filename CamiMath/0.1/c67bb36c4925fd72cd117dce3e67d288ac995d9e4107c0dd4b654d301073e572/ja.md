```
polynom_product(polynom1, polynom2)
```

2つの多項式の積の係数、a = `polynom1` と b = `polynom2` の次数 $m$ と $n$ に対して、次元 $d=m+n+1$ のベクトル空間における多項式を表します。

$$
    P(x)=a_0b_0 + (a_0b_1 + b_0a_1)x + ⋯ + a_n b_m x^{n+m}.
$$

#### 例:

```
julia> polynom_product((1, 1), (1, -1, 2))
4-element Vector{Int64}:
 1
 0
 1
 2

julia> polynom_product((1, 1), (1, -1.0, 2))
4-element Vector{Real}:
 1
 0.0
 1.0
 2  
```
