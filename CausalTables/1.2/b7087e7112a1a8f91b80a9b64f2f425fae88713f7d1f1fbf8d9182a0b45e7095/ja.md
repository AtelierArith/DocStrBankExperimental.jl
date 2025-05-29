```
condensity(scm::StructuralCausalModel, ct::CausalTable, name::Symbol)
```

構造的因果モデル `scm` から引き出された因果テーブル `ct` における変数 `name` の条件付き密度を計算します。

# 引数

  * `scm::StructuralCausalModel`: データ生成プロセスを表す構造的因果モデル。
  * `ct::CausalTable`: 観測データを含む因果テーブル。
  * `name::Symbol`: 条件付き密度を計算する変数。

# 戻り値

観測データに基づく変数 `var` の条件付き密度。
