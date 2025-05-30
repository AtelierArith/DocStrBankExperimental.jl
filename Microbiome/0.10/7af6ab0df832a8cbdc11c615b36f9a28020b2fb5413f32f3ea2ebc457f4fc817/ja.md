```
MicrobiomeSample(name::String, metadata::Dictionary{Symbol, T}) <: AbstractSample
MicrobiomeSample(name::String; kwargs...)
MicrobiomeSample(name::String)
```

名前と任意のメタデータの[`Dictionary`](https://github.com/andyferris/Dictionaries.jl)を含むマイクロバイオームサンプルタイプで、`Symbol`（`:name`や`:metadata`以外）をキーとして使用します。

メタデータは、サンプル自体に対して`getproperty`または`getindex`を使用してアクセスできます。

サンプルは名前のみでインスタンス化でき、`metadata`の`Dictionary`は空白のままにできます。

メタデータの追加や変更は、通常の`Dictionary`と同じルールに従います。[こちら](https://github.com/andyferris/Dictionaries.jl#accessing-dictionaries)を参照してください。
