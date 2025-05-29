```
AbstractBlackboxIdeal
```

`K(x)[y]` のブラックボックスイデアルで、`x` で評価可能です。

## インターフェース

`AbstractBlackboxIdeal` のサブタイプは、以下の関数を実装する必要があります：

  * `length(<:AbstractBlackboxIdeal)`: イデアル生成子の数。
  * `base_ring(<:AbstractBlackboxIdeal)`: 元の基底体。
  * `parent(<:AbstractBlackboxIdeal)`: 元の多項式環。
  * `parent_params(<:AbstractBlackboxIdeal)`: 係数の元の多項式環。
  * `reduce_mod_p!(<:AbstractBlackboxIdeal, finite_field)`: 生成子を `p` で剰余計算します。ここで `p` は与えられた `finite_field` の特性です。
  * `specialize_mod_p(<:AbstractBlackboxIdeal, point)`: `point` でイデアルを特化し、Zp[y] における特化されたイデアルの生成子を返します。
