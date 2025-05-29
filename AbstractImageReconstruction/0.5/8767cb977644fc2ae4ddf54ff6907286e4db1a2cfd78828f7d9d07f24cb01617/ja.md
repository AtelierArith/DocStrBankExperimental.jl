```
toKwargs(value::AbstractImageReconstructionParameters; kwargs...)
```

`AbstractImageReconstructionParameters`を各プロパティの`Dict{Symbol, Any}`に変換します。

オプションのキーワード引数:

  * flatten::Vector{DataType}: フラット化する型。デフォルトでは`AbstractImageReconstructionParameters`のみがフラット化されます。
  * ignore::Vector{Symbol}: 無視するプロパティ。
  * default::Dict{Symbol, Any}: 欠落しているプロパティのデフォルト値。
  * overwrite::Dict{Symbol, Any}: プロパティの値を上書きします。
