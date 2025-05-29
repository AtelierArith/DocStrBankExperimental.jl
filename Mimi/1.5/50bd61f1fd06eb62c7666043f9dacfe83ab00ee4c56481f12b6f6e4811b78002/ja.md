```
connect_param!(m::Model, comp_name::Symbol, param_name::Symbol, model_param_name::Symbol;
               check_attributes::Bool=true, ignoreunits::Bool=false))
```

コンポーネント `comp_name` のパラメータ `param_name` を複合体 `obj` のモデルパラメータ `model_param_name` に接続します。
