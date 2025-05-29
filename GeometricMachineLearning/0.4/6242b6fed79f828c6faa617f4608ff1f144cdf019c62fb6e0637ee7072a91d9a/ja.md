```
PSDArch <: SymplecticCompression
```

`PSDArch`は[`PSDLayer`](@ref)に対応するアーキテクチャです。

## アーキテクチャ

適切なシンプレクティック分解（PSD）は、デコーダーとエンコーダーの両方がPSDのような行列である[`SymplecticAutoencoder`](@ref)として見ることができます（[`PSDLayer`](@ref)のドキュメントを参照）。

## トレーニング

このアーキテクチャのパラメータを最適化するために、ニューラルネットワークのトレーニングは必要ありません（[`solve!`](@ref)のドキュメントを参照）。

## コンストラクタ

コンストラクタは、入力として2つの引数のみを受け取ります：

  * `full_dim::Integer`
  * `reduced_dim::Integer`
