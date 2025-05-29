```
PipeGet{name}()
```

A special pipeline that get the wanted `name`s from namedtuple.

# Example

```julia-repl
julia> p = Pipeline{:x}(identity, 1) |> Pipeline{(:sinx, :cosx)}(sincos, 1) |> PipeGet{(:x, :sinx)}()
Pipelines:
  target[x] := identity(source)
  target[(sinx, cosx)] := sincos(source)
  target := (target.x, target.sinx)

julia> p(0.5)
(x = 0.5, sinx = 0.479425538604203)

julia> p = Pipeline{:x}(identity, 1) |> Pipeline{(:sinx, :cosx)}(sincos, 1) |> PipeGet{:sinx}()
Pipelines:
  target[x] := identity(source)
  target[(sinx, cosx)] := sincos(source)
  target := (target.sinx)

julia> p(0.5)
0.479425538604203

```
