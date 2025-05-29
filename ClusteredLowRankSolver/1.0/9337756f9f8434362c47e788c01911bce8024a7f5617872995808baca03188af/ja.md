```
Constraint(constant, matrixcoeff, freecoeff[, samples, scalings])
```

多項式制約を次の形でモデル化します

$$
    ∑_i ⟨ A_i(x), Y_i  ⟩ + ∑_j b_j(x) y_j = c(x)
$$

`samples`に基づいています。ここで、$A_i$、$b_j$、および$c$が多項式である場合にのみ、サンプルが必要です。係数行列$A_i$が同じサイズのブロック構造を持つ場合、`Block`構造体をキーとして使用して、与えられた行列がどのサブブロックに対応するかを示すことができます。

引数:

  * `constant`: 右辺$c(x)$
  * `matrixcoeff::Dict`: 正定値行列変数の係数行列。
  * `freecoeff::Dict`: 自由変数の係数。
  * `samples::Vector`: 制約が満たされるべきサンプルセット。多項式制約に必要です。
  * `scalings::Vector`: オプション; サンプルインデックスに依存する係数で制約をスケールします。

```
