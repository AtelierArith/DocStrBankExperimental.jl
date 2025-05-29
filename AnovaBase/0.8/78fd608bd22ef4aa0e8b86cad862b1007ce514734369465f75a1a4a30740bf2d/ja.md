```
MixedAovModels{M, N} <: AnovaModel{M, N}
```

ANOVAを実施するための複数のタイプのネストされたモデルのラッパーです。

  * `M` は回帰モデルのユニオン型です。
  * `N` はモデルの数です。

# フィールド

  * `model`: モデルのタプル。

# コンストラクタ

```
MixedAovModels{M}(model...) where M 
MixedAovModels{M}(model::T) where {M, T <: Tuple}
```
