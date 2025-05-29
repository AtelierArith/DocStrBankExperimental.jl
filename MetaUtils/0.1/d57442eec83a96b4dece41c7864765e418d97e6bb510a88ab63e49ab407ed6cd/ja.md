```
@teval texpr
```

は、lispのようなタプル式 `texpr` を評価します。

例: `sin(π/6)` の計算

```julia
julia> @teval (:call, :sin, (:call, :/, π, 6))
0.49999999999999994
```

場合によっては、`:call` を省略することができます。

```julia
julia> @teval (:sin, (:/, π, 6))
0.49999999999999994
```
