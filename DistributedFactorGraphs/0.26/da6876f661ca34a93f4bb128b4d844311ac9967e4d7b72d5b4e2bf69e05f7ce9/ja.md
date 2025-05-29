```julia
updateVariableSolverData!(dfg, variablekey, vnd; ...)
updateVariableSolverData!(
    dfg,
    variablekey,
    vnd,
    useCopy;
    ...
)
updateVariableSolverData!(
    dfg,
    variablekey,
    vnd,
    useCopy,
    fields;
    warn_if_absent
)

```

存在する場合は変数ソルバーデータを更新し、そうでない場合は追加します。

ノート：

  * `useCopy=true` はソルバーデータをコピーし、別のメモリを保持します。
  * `fields` を使用して、`useCopy` に従いながら、いくつかの VND.fields のみを更新します。

関連

mergeVariableSolverData!
