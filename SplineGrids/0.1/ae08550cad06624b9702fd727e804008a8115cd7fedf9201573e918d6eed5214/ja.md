```
KnotVector(
    n_basis_functions::Integer, 
    degree::Integer; 
    extent::Tuple{Number, Number} = (0,1), 
    distribution::Symbol = :equispaced)
```

クランプされたノットベクターを構築します。すなわち、最初と最後のノットの重複度は degree + 1 であり、他の重複度は 1 です。

## 引数

  * `n_basis_functions`: このノットベクター上で定義される基底関数の数
  * `degree`: このノットベクター上で定義される基底関数の次数

## キーワード引数

  * `extent`: ノットベクターの範囲を定義するタプル (t*min, t*max)
  * `distribution`: 内部ノットの分布。選択肢は :equispaced または :random
  * `backend`: オブジェクト内の配列の KernelAbstractions バックエンド。デフォルトは `CPU()`。
  * `float_type`: すべての浮動小数点配列の型。デフォルトは `Float32`。
  * `int_type`: すべての整数配列の型。デフォルトは `Int32`。
