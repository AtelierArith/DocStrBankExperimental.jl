```
CompressionStrategy
```

`CompressionStrategy`は、ステップ後にベクトルがどのように圧縮されるかを制御します。

## デフォルトの実装:

  * [`NoCompression`](@ref): ベクトル圧縮なし

## 使用法

`CompressionStrategy`のサブタイプは、いくつかの[`StochasticStyle`](@ref)のコンストラクタにキーワード引数として渡すことができます。`CompressionStrategy(s::StochasticStyle)`を呼び出すと、関連するサブタイプが返されます。デフォルトは[`NoCompression`](@ref)です。

## インターフェース

新しい`CompressionStrategy`を定義する際は、`MyCompressionStrategy <: CompressionStrategy`としてサブタイプ化し、これらのメソッドを定義します:

  * [`compress!(s::CompressionStrategy, v)`](@ref compress!)
  * [`compress!(s::CompressionStrategy, w, v)`](@ref compress!)
  * [`step_stats(s::CompressionStrategy)`](@ref step_stats)
