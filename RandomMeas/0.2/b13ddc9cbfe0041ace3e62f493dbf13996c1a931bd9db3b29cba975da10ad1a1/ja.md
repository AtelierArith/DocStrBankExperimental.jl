```
get_expect_shadow(O::MPO, shadows::AbstractArray{<:AbstractShadow}; compute_sem::Bool = false)
```

MPO演算子`O`の平均期待値をシャドウオブジェクトの配列を使用して計算します。

# 引数

  * `O::MPO`: 期待値を計算するMPO演算子。
  * `shadows::AbstractArray{<:AbstractShadow}`: 期待値が計算されるシャドウオブジェクトの配列（任意の形状）。
  * `compute_sem::Bool`（オプション）: `true`の場合、平均の標準誤差（SEM）も計算します。デフォルトは`false`です。

# 戻り値

  * `compute_sem`が`false`の場合、平均期待値を返します。
  * `compute_sem`が`true`の場合、タプル`(mean, sem)`を返します。ここで、`mean`は平均期待値、`sem`は標準誤差です。

# 例

```julia
mean_val = get_expect_shadow(O, shadows)
mean_val, sem_val = get_expect_shadow(O, shadows; compute_sem=true)
```
