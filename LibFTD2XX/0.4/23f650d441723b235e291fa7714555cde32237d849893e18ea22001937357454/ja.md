```
status(d::D2XXDevice) ->
  mflaglist::Dict{String, Bool}, lflaglist::Dict{String, Bool}
```

オープンされた [`FT_HANDLE`](@ref) に対して、モデムステータス (`mflaglist`) とラインステータス (`lflaglist`) のフラグの `Bool` 辞書を返します。これは [`FT_GetModemStatus`](@ref) を使用します。

関連情報: [`isopen`](@ref), [`open`](@ref)
