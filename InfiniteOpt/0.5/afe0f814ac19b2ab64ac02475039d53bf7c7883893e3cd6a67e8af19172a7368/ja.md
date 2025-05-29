```
set_supports(
    prefs::Union{Vector{GeneralVariableRef}, AbstractArray{<:GeneralVariableRef}},
    supports::Union{Array{<:Real, 2}, Vector{<:AbstractArray{<:Real}}};
    [force::Bool = false]
    )::Nothing
```

依存する無限パラメータ `prefs` に関連付けられたサポートポイントを設定します。`prefs` が依存する無限パラメータでない場合、`ArgumentError` がスローされます。
