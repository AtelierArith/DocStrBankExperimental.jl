```julia
inpolygon(x,y,point)
```

2Dポリゴンが配列 `x` と `y` によって定義される場合、指定された `point` が含まれているかどうかを確認します。ブール値（true または false）を返します。

### 例

```julia
julia> x = [0, 1, 1, 0];

julia> y = [0, 0, 1, 1];

julia> inpolygon(x, y, (0.5,0.5))
true

julia> inpolygon(x, y, (0.5,1.5))
false
```
