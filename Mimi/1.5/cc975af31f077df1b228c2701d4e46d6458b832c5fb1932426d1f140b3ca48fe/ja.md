```
set_param!(md::ModelDef, comp_name::Symbol,
           value_dict::Dict{Symbol, Any}, param_names)
```

`set_param!()`を`param_names`の各名前に対して呼び出し、`value_dict[param_name]`から対応する値を取得します。
