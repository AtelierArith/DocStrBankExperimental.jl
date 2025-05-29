```
rand(scm::StructuralCausalModel, n::Int)
```

指定されたサンプル数を使用して構造的因果モデル（SCM）からランダムデータを生成します。

# 引数

  * `scm::StructuralCausalModel`: データを生成するための構造的因果モデル。
  * `n::Int`: 生成するサンプルの数。

# 戻り値

生成されたデータを含む `CausalTable` オブジェクト。
