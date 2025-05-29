```
disconnect_param!(obj::AbstractCompositeComponentDef, comp_def::AbstractComponentDef, param_name::Symbol)
```

与えられたコンポーネント `comp_def` において、指定されたパラメータ `param_name` の接続を削除します。`comp_def` はコンポジット `obj` の直接のサブコンポーネントでなければなりません。
