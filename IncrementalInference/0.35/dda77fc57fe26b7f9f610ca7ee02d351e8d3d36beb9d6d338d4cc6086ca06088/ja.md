```julia
ensureSolvable!(dfg; solvableTarget, solvableFallback)

```

`solvable=1`として設定された変数が、接続された`solvable=1`の因子なしに浮遊していないことを確認します。もし見つかった場合、その「自由」変数の`solvable=solvableFallback`（デフォルトは`0`）に設定します。

関連

[`initAll!`](@ref)
