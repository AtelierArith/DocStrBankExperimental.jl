```
NestedModels{M, N} <: AnovaModel{M, N}
```

同じタイプのネストされたモデルのラッパーで、ANOVAを実施します。

  * `M` は回帰モデルのタイプです。
  * `N` はモデルの数です。

# フィールド

  * `model`: モデルのタプル。

# コンストラクタ

```
NestedModels(model::Vararg{M, N}) where {M, N}
NestedModels(model::NTuple{N, M}) where {M, N}
```
