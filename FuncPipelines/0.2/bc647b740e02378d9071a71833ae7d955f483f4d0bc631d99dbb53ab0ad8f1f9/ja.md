```
PipeVar{name}(x)
```

特別なパイプラインで、`x`を名前付きタプルの`name`として設定します。

# 例

```julia-repl
julia> p = Pipeline{:x}(identity, 1) |> PipeVar{:y}(5) |> Pipeline{:z}(+, (:x, :y))
Pipelines:
  target[x] := identity(source)
  target[y] := 5
  target[z] := +(target.x, target.y)

julia> p(3)
(x = 3, y = 5, z = 8)

```
