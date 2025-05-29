```
polynom_product_expansion(polynom1, polynom2, p::Int)
```

2つの多項式の積の係数、a = `polynom1`（次数 $n$）と b = `polynom2`（次数 $m$）、を次数 `p` で切り捨てたもので、次元 $d=p+1$ のベクトル空間における多項式を表します。

#### 例:

```
julia> a = (1,-1,1);

julia> b = (1,1,-1,1,1,1);

julia> o = polynom_product(a, b); println(o)
[1, 0, -1, 3, -1, 1, 0, 1]
 
julia> o = polynom_product_expansion(a, b, 4); println(o)
[1, 0, -1, 3, -1] 
```
