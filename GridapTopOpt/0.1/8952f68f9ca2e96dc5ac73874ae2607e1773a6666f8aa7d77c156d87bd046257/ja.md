```
struct AffineFEStateMap{A,B,C,D,E,F} <: AbstractFEStateMap
```

アフィン有限要素演算子 `AffineFEOperator` のための前方問題とプルバックを有効にする構造体です。

# パラメータ

  * `biform::A`: 双線形形式を定義する `IntegrandWithMeasure`。
  * `liform::B`: 線形形式を定義する `IntegrandWithMeasure`。
  * `spaces::C`: 有限要素空間の `Tuple`。
  * `plb_caches::D`: プルバック演算子のためのキャッシュ。
  * `fwd_caches::E`: 前方問題のためのキャッシュ。
  * `adj_caches::F`: 隣接問題のためのキャッシュ。
