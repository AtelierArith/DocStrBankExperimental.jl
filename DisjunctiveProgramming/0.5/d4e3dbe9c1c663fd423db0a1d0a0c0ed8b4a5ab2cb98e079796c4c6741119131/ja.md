```
binary_variable(vref::LogicalVariableRef)::JuMP.AbstractVariableRef
```

論理変数 `vref` の基になるバイナリ変数を返します。これは再定式化されたモデルで使用されます。これは、論理変数を代数的制約に埋め込むのに役立ちます。
