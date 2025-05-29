```
AbstractLPCMFormat
```

Ondaの標準インタリーブLPCM表現に対して（デ）シリアライズ可能なバイト/ストリームフォーマットを表すサブタイプを持つ型です。

`F<:AbstractLPCMFormat`のすべてのサブタイプは、[`Onda.register_lpcm_format!`](@ref)を呼び出し、適切な[`file_format_string`](@ref)メソッドを定義する必要があります。

参照：

  * [`format`](@ref)
  * [`deserialize_lpcm`](@ref)
  * [`deserialize_lpcm_callback`](@ref)
  * [`serialize_lpcm`](@ref)
  * [`LPCMFormat`](@ref)
  * [`LPCMZstFormat`](@ref)
  * [`AbstractLPCMStream`](@ref)
