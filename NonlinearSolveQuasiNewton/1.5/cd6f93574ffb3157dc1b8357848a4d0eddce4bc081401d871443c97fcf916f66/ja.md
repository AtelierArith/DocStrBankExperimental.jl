```
LimitedMemoryBroyden(;
    max_resets::Int = 3, linesearch = nothing, threshold::Val = Val(10),
    reset_tolerance = nothing, alpha = nothing
)
```

`LimitedMemoryBroyden` [ziani2008autoadaptative](@cite) の実装で、リセットとラインサーチを行います。

### キーワード引数

  * `max_resets`: 実行するリセットの最大数。デフォルトは `3` です。
  * `reset_tolerance`: リセットチェックのための許容誤差。デフォルトは `sqrt(eps(real(eltype(u))))` です。
  * `threshold`: 低ランク近似に保存するベクトルの数。デフォルトは `Val(10)` です。
  * `alpha`: 初期ヤコビ行列の逆行列は `(αI)⁻¹` に設定されます。デフォルトは `nothing` で、これは `α = max(norm(u), 1) / (2 * norm(fu))` を意味します。
