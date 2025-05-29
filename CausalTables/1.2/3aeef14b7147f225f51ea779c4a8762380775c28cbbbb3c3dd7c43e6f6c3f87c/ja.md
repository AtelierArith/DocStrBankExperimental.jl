```
propensity(scm::StructuralCausalModel, ct::CausalTable, name::Symbol)
```

変数 `name` の (一般化された) 傾向スコアを、StructuralCausalModel `scm` から引き出された CausalTable `ct` で計算します。

# 引数

  * `scm::StructuralCausalModel`: データ生成プロセスを表す StructuralCausalModel オブジェクト。
  * `ct::CausalTable`: データを表す CausalTable オブジェクト。
  * `name::Symbol`: 条件付き平均を計算する変数。

# 戻り値

指定された変数の条件付き確率の配列 (または、指定された変数が連続の場合は密度)。
