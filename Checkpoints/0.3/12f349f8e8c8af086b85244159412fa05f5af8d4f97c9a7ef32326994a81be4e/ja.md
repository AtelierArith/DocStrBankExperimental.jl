```
checkpoint_fullname(x::IndexEntry)
```

チェックポイント出力ファイルのフルネームで、[`prefixes`](@ref)および[`checkpoint_name`](@ref)を含みます。チェックポイントが`checkpoint(Forecasters, "forecasts", ...)`を使用して保存された場合、`checkpoint_fullname`は`"Forecasters.forecasts"`を返します。チェックポイントが`checkpoint("Foo.Bar", "forecasts.jlso")`を使用して保存された場合、`checkpoint_fullname`は`"Foo.Bar.forecasts"`を返します。
