```
PipeVar{name}(x)
```

A special pipeline that set `x` as `name` to the namedtuple.

# Example

```julia-repl
julia> p = Pipeline{:x}(identity, 1) |> PipeVar{:y}(5) |> Pipeline{:z}(+, (:x, :y))
Pipelines:
  target[x] := identity(source)
  target[y] := 5
  target[z] := +(target.x, target.y)

julia> p(3)
(x = 3, y = 5, z = 8)

```
