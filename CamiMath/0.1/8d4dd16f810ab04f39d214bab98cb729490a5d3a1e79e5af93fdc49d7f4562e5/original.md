```
triangle_coefficient(a::Real, b::Real, c::Real)
```

Triangle coefficient for a triangle of sides `a`, `b` and `c`,

$$
    \Delta(abc)\equiv\frac{(a+b-c)!(b+c-a)!(c+a-b)!}{(a+b+c+1)!}
$$

Triangle condition satisfied for $\Delta > 0$

#### Examples:

```
julia> triangle_coefficient(3, 4, 5)
1//180180

julia> triangle_coefficient(1//2, 1, 1.5)
1//12
```
