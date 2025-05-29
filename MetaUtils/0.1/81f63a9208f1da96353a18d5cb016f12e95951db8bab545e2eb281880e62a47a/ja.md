```
teval(texpr, m::Module=Main)
```

は、lispのようなタプル式 `texpr` を評価します。

例: `sin(π/6)` の計算

```julia
julia> (:call, :sin, (:call, :/, π, 6)) |> teval
0.49999999999999994
```

場合によっては、`:call` を省略することができます。

```julia
julia> (:sin, (:/, π, 6)) |> teval
0.49999999999999994
```
