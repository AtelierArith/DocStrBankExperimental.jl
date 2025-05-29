```
y, t, x = step(sys[, tfinal])
y, t, x = step(sys[, t])
```

システム `sys` の応答を時間 `t = 0` での単位ステップに対して計算します。最終時間 `tfinal` または時間ベクトル `t` が提供されていない場合、システムの極の位置に基づいて計算されます。

返り値は `SimResult` 型の構造体です。`SimResult` は `plot(result)` でプロットすることができ、または `y, t, x = result` のように分解することができます。

`y` のサイズは `(ny, length(t), nu)` であり、`x` のサイズは `(nx, length(t), nu)` です。

[`stepinfo`](@ref) および [`lsim`](@ref) も参照してください。
