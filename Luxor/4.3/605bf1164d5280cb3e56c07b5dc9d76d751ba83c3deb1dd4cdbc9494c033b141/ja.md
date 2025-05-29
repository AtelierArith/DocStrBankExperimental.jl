```
@polar (p)
```

2つの数のタプルをx, yデカルト座標のPointに変換します。

```julia
julia> @polar 10, pi/4
Point(7.0710678118654755, 7.071067811865475)
```

使用例

```julia
@polar (10, pi/4)
@polar [10, pi/4]
@polar 10, pi/4
```
