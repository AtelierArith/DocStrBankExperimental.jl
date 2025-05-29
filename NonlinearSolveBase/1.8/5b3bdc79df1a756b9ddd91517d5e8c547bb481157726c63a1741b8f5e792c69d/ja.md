```
step!(
    cache::AbstractNonlinearSolveCache;
    recompute_jacobian::Union{Nothing, Bool} = nothing
)
```

非線形ソルバーの1ステップを実行します。

### キーワード引数

  * `recompute_jacobian`: 現在のステップでヤコビアンを再計算するかどうかを制御します。`nothing`の場合、アルゴリズムはヤコビアンを再計算するかどうかを判断します。`true`または`false`の場合、ヤコビアンはそれぞれ再計算されるか再計算されません。ヤコビアン情報を使用しないアルゴリズムの場合、このキーワードは一度だけ警告とともに無視されます。
