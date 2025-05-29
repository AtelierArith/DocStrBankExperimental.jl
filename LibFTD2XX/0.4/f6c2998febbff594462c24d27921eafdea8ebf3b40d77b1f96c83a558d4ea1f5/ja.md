```
status(d::D2XXDevice) ->
  mflaglist::Dict{String, Bool}, lflaglist::Dict{String, Bool}
```

オープンされた [`D2XXDevice`](@ref) に対して、モデムステータス (`mflaglist`) とラインステータス (`lflaglist`) のフラグの `Bool` 辞書を返します。これは [`FT_GetModemStatus`](@ref) を使用して行います。
