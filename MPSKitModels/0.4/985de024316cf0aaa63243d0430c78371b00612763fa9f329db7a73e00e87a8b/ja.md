```
@mpoham(block)
```

ローカル演算子の和で表される行列積演算子を指定します。

このマクロは、`O{i...}` の形式の式を、`O` が演算子であり、`i` が整数または格子点であるサイト `i...` に作用する演算子に変換します。このマクロは、以下の形式の式を認識します：

  * `O{i...}` は、サイト `i...` に作用するローカル演算子 `O` を示します。
  * `-Inf:Inf`、`-∞:∞`、`-Inf:step:Inf`、`-∞:step:∞` は、無限鎖を示します。
  * `1:L` は、有限鎖を示します。
  * `∑` は、和を表します。

# 例

```julia
H_ising = @mpoham sum(σᶻᶻ{i, i+1} + h * σˣ{i} for i in -Inf:Inf)
H_heisenberg = @mpoham ∑(sigma_exchange(){i,j} for (i,j) in nearest_neighbours(-∞:∞))
```
