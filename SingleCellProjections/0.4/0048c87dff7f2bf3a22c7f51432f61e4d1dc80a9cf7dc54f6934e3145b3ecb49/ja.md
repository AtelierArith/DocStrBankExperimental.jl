```
DataMatrix(matrix, var, obs; kwargs...)
```

与えられた `matrix`、`var`、および `obs` を使用して `DataMatrix` を作成します。

`var`/`obs` の最初の列は ID として使用されます。

Kwargs:

  * `duplicate_var` - 重複する var ID が見つかった場合に何が起こるかを決定するために `:ignore`、`:warn`、または `:error` に設定します。
  * `duplicate_obs` - 重複する obs ID が見つかった場合に何が起こるかを決定するために `:ignore`、`:warn`、または `:error` に設定します。
