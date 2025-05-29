```
add_supports(
    prefs::Union{Vector{GeneralVariableRef}, AbstractArray{<:GeneralVariableRef}},
    supports::Union{Array{<:Real, 2}, Vector{<:AbstractArray{<:Real}}}
    )::Nothing
```

依存する無限パラメータ `prefs` にサポートポイント `supports` を追加します。`prefs` が依存する無限パラメータでない場合、`ArgumentError` がスローされます。
