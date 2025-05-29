```
polynomial(polynom, x::T [; deriv=0]) where T<:Real
```

次数 $d$ の多項式、

$$
    P(x)=c_0 + c_1 x + ⋯ + c_d x^d,
$$

ここで、係数 `polynom` = $(c_0,⋯\ c_d)$ は次元 $d+1$ のベクトル空間における多項式のベクトル表現を定義します。

#### 例:

```
julia> polynom = (1, 1, 1, 1, 1);
           
julia> P(x) = polynomial(polynom,x);

julia> P(1)
5

julia> polynomial(polynom, 1; deriv=1)     # P′(1)
10

julia> polynomial(polynom, 2; deriv=2)     # P″(1)
20

julia> polynomial(polynom, 1; deriv=-1)   # 原始関数 (定数項はゼロ)
137 // 60
```
