```
RKOCEvaluatorMFV{S,T,N}(
    trees::AbstractVector{LevelSequence},
) -> RKOCEvaluatorMFV{S,T,N}
```

与えられた根付き木のリストをエンコードする `RKOCEvaluatorMFV` を構築します。

標準の `RKOCEvaluator` とは異なり、ステージの数 `S` は静的型パラメータとして提供され、SIMD ベクター幅を静的に決定します。

# 引数

  * `trees`: `LevelSequence` 表現での根付き木の入力リスト。

型 `T` が指定されていない場合、デフォルトは `Float64` です。
