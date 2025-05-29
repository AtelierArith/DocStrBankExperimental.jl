```
get_count(ams::AbstractManoptSolverState, ::Symbol)
```

特定の可算サイズのカウントを取得します。例えば、`:Iterations`。この関数は、カウントするものがなかった場合は0を返します。

ソルバー状態内で利用可能なシンボル

  * `:Iterations` は、ソルバーが停止したイテレーションを取得するために `stop` フィールドに渡されます。
