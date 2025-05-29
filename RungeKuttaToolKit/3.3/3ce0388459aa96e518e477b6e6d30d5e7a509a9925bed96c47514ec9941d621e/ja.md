```
RKOCEvaluatorSIMD{S,T}(
    trees::AbstractVector{LevelSequence},
) -> RKOCEvaluatorSIMD{S,T}
```

与えられた根付き木のリストをエンコードする `RKOCEvaluatorSIMD` を構築します。

標準の `RKOCEvaluator` とは異なり、段階数 `S` は静的型パラメータとして提供され、静的にSIMDベクトル幅を決定します。

# 引数

  * `trees`: `LevelSequence` 表現での根付き木の入力リスト。

型 `T` が指定されていない場合、デフォルトは `Float64` です。
