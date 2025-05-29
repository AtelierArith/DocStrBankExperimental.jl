```
struct RydInteract{D} <: AbstractTerm{D}
RydInteract(;atoms, C=2π * 862690MHz⋅μm^6)
```

ライデバーグ相互作用項の型。

# 表現

$$
\sum_{i, j} \frac{C}{|x_i - x_j|^6} n_i n_j
$$

# キーワード引数

  * `atoms`: 原子の位置のリストで、型は `RydAtom` でなければならず、デフォルト単位は `μm` です。
  * `C`: 相互作用の強さで、デフォルト単位は `MHz⋅μm^6` です。デフォルト値は `2π * 862690 * MHz*µm^6` です。
