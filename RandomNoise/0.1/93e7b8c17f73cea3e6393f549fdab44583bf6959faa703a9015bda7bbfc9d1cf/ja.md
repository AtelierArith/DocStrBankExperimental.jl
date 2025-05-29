```
NoiseMap{T,N,R,F}
```

`N`次元の無限のランダム値のストリーム。

# フィールド

  * `noise` 基本のランダム数のストリームを生成するために使用されるノイズ関数
  * `transform` ノイズ関数の出力に適用され、結果を得るための関数

変換は次のようにできます。

  * 任意の関数
  * `NoiseUniform` のインスタンス。この場合、値は区間 [0,1) に一様に分布する浮動小数点数です。
  * `Distributions.UnivariateDistribution` のインスタンス。この場合、値はその分布からのサンプルです。

# 例

```jldoctest
julia> nm = NoiseMap(sqn)
NoiseMap{UInt32, 1, SquirrelNoise5, typeof(identity)}(SquirrelNoise5(0x00000000), identity)
```
