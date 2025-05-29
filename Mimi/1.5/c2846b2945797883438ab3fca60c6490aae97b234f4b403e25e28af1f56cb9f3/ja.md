```
connect_param!(obj::AbstractCompositeComponentDef, comp_def::AbstractComponentDef,
                param_name::Symbol, model_param_name::Symbol; check_attributes::Bool=true,
                ignoreunits::Bool = false)
```

コンポジット `obj` のコンポーネント `comp_def` にあるパラメータ `param_name` をモデルパラメータ `model_param_name` に接続します。
