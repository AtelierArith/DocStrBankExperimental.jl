```
format(file_format::AbstractString, info; kwargs...)
```

`f(info; kwargs...)`を返します。ここで、`f`は`file_format`に対応する`AbstractLPCMFormat`インスタンスを構築し、infoは[`SamplesInfoV2`](@ref)準拠の値です。`f`は、`file_format`を[`register_lpcm_format!`](@ref)を介して登録された適切なフォーマットコンストラクタにマッチさせることによって決定されます。

関連情報: [`deserialize_lpcm`](@ref), [`serialize_lpcm`](@ref)
