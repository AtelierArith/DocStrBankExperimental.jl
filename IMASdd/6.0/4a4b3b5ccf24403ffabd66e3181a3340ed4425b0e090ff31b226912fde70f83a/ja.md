```
Base.setproperty!(@nospecialize(ids::IDS), field::Symbol, value::AbstractArray{<:IDS}; skip_non_coordinates::Bool=false, error_on_missing_coordinates::Bool=true)
```

IDS構造体の全ベクトルのsetpropertyを一度に処理します（ids.fieldはIDSvector型です）
