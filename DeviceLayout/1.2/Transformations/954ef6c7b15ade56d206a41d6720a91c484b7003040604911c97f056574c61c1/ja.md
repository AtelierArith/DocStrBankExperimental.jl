```
XReflection()
```

x軸に関する反射を構築します（y座標の符号が変わります）。

例：

```jldoctest
julia> trans = XReflection()
LinearMap([1 0; 0 -1])

julia> trans(Point(1, 1))
2-element Point{Int64} with indices SOneTo(2):
  1
 -1
```
