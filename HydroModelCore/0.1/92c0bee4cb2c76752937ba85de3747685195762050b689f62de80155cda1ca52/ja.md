```
get_var_names(funcs::Vector{<:AbstractFlux}, dfuncs::Vector{<:AbstractStateFlux})
```

フラックスおよび状態フラックス関数からすべての変数名を取得します。返される値は (input*names, output*names, state_names) です。
