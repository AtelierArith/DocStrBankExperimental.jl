```
JuMP.add_to_function_constant(cref::InfOptConstraintRef, value::Real)::Nothing
```

`value`を関数定数項に追加します。スカラー制約の場合、JuMPはすべての定数項を制約の右辺に集約するため、関数を修正するのではなく、集合は`-value`によって変換されます。例えば、制約`2x <= 3`がある場合、`add_to_function_constant(c, 4)`はそれを`2x <= -1`に修正します。```
