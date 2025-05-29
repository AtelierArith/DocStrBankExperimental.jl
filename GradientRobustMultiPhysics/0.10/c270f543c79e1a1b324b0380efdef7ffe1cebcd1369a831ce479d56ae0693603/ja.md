```julia
abstract type AbstractFiniteElement
```

再構成同一性演算子: 再構成された有限要素関数のバージョンを評価します。

FEreconstは、適用される有限要素に対して定義されている場合、再構成空間と再構成アルゴリズムを指定します。
