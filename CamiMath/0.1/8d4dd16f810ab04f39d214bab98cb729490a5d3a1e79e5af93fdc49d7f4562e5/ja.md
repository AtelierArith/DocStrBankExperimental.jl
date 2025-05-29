```
triangle_coefficient(a::Real, b::Real, c::Real)
```

三角形の辺 `a`、`b`、`c` に対する三角形係数、

$$
    \Delta(abc)\equiv\frac{(a+b-c)!(b+c-a)!(c+a-b)!}{(a+b+c+1)!}
$$

三角形条件は $\Delta > 0$ の場合に満たされます

#### 例:

```
julia> triangle_coefficient(3, 4, 5)
1//180180

julia> triangle_coefficient(1//2, 1, 1.5)
1//12
```
