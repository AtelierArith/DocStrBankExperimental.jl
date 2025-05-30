```
AbstractBlackboxIdeal
```

`K(x)[y]` のブラックボックス理想で、`x` で評価可能です。

## インターフェース

`AbstractBlackboxIdeal` のサブタイプは、以下の関数を実装する必要があります：

  * `length(<:AbstractBlackboxIdeal)`: 理想生成元の数。
  * `base_ring(<:AbstractBlackboxIdeal)`: 元の基底体。
  * `parent(<:AbstractBlackboxIdeal)`: 元の多項式環。
  * `parent_params(<:AbstractBlackboxIdeal)`: 係数の元の多項式環。
  * `reduce_mod_p!(<:AbstractBlackboxIdeal, finite_field)`: 生成元を `p` で剰余計算します。ここで `p` は与えられた `finite_field` の特性です。
  * `specialize_mod_p(<:AbstractBlackboxIdeal, point)`: `point` で理想を特化し、Zp[y] における特化された理想の生成元を返します。
