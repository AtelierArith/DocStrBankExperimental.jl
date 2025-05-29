```
dispatch_variable_ref(vef::GeneralVariableRef)::DispatchVariableRef
```

`vref` に関連付けられた具体的な [`DispatchVariableRef`](@ref) を返します。これは、インデックス型に対して `dispatch_variable_ref` が拡張されていることに依存しており、そうでない場合は `MethodError` がスローされます。
