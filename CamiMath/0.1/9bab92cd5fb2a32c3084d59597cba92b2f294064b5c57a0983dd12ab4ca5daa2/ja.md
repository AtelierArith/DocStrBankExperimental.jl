```
istriangle(a::Real, b::Real, c::Real)
```

辺 `a`、`b`、`c` の三角形の条件。

#### 例:

```
julia> istriangle(3, 4, 5)
true

julia> istriangle(1//2, 1, 1.5)
true
```
