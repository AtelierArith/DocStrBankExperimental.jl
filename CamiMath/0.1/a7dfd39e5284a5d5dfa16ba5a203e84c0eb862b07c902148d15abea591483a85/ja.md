```
polynom_power(polynom, p)
```

`polynom` は、次数 $d$ の多項式を `p` 乗したもので、次元 $p d + 1$ のベクトル空間における多項式を定義します。

#### 例:

```
julia> polynom = (1,1,1)    # 次数 d = 2 の多項式ベクトルの座標
(1, 1, 1)

julia> polynom = (1,1,1);

julia> polynom_power(polynom, 3)
7-element Vector{Int64}:
 1
 3
 6
 7
 6
 3
 1
```
