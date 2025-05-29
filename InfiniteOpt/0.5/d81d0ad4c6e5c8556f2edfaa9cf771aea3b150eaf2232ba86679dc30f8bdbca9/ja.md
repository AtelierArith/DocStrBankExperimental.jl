```
JuMP.delete(model::InfiniteModel,
            prefs::AbstractArray{<:GeneralVariableRef})::Nothing
```

`JuMP.delete`を拡張して、依存する無限パラメータのグループとその依存関係を削除します。`prefs`が依存する無限パラメータでない場合、`ArgumentError`がスローされます。
