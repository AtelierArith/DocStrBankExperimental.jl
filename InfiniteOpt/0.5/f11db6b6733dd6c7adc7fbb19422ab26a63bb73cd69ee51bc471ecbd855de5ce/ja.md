```
add_supports(pref::GeneralVariableRef,
             supports::Union{Real, Vector{<:Real}})::Nothing
```

単一の無限パラメータ `pref` にサポートポイント `supports` を追加します。`pref` が独立した無限パラメータでない場合、`ArgumentError` がスローされます。
