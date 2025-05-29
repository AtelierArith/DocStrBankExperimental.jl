```
convar(scm::StructuralCausalModel, ct::CausalTable, name::Symbol)
```

構造的因果モデル `scm` から引き出された因果テーブル `ct` における変数 `name` の条件付き分散を計算します。

# 引数

  * `scm::StructuralCausalModel`: データ生成プロセスを表す構造的因果モデルオブジェクト。
  * `ct::CausalTable`: データを表す因果テーブルオブジェクト。
  * `name::Symbol`: 条件付き平均を計算する変数。

# 戻り値

指定された変数の条件付き分散の配列。
