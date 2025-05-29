```
struct NonlinearFEStateMap{A,B,C,D,E,F} <: AbstractFEStateMap
```

非線形有限要素演算子の前方問題とプルバックを可能にする構造体です。

# パラメータ

  * `res::A`: 問題の残差を定義する `IntegrandWithMeasure`。
  * `jac::B`: 残差のヤコビアンを定義する `Function`。
  * `spaces::C`: 有限要素空間の `Tuple`。
  * `plb_caches::D`: プルバック演算子のキャッシュ。
  * `fwd_caches::E`: 前方問題のキャッシュ。
  * `adj_caches::F`: 隣接問題のキャッシュ。
