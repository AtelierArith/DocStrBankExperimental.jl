```
disconnect_param!(obj::AbstractCompositeComponentDef, comp_name::Symbol, param_name::Symbol)
```

与えられたコンポーネント `comp_def` において、指定されたパラメータ `param_name` の接続を削除します。このコンポーネントは、コンポジット `obj` の直接のサブコンポーネントでなければなりません。
