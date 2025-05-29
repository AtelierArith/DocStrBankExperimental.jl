```
update_param!(obj::AbstractCompositeComponentDef, name::Symbol, value; update_timesteps = nothing)
```

コンポジット `obj` 内のモデルパラメータの `value` を、`name` で参照して更新します。`update_timesteps` キーワード引数は非推奨であり、警告を提供するためにここに残しています。
