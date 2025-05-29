```
struct RepeatingAffineFEStateMap <: AbstractFEStateMap
```

アフィン有限要素演算子 `AffineFEOperator` のための前方問題とプルバックを可能にする構造体で、複数の線形形式を持ちますが、単一の双線形形式のみを持ちます。

# パラメータ

  * `biform`: 双線形形式を定義する `IntegrandWithMeasure`。
  * `liform`: 線形形式を定義する `IntegrandWithMeasure` のベクトル。
  * `spaces`: 繰り返し有限要素空間。
  * `spaces_0`: 繰り返される元の有限要素空間。
  * `plb_caches`: プルバック演算子のキャッシュ。
  * `fwd_caches`: 前方問題のキャッシュ。
  * `adj_caches`: 隣接問題のキャッシュ。
