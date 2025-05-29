```
get_expect_shadow(O::MPO, shadow::AbstractShadow)
```

MPO演算子`O`の期待値を単一のシャドウオブジェクトを使用して計算します。

# 引数:

  * `O::MPO`: 期待値が計算されるMPO演算子。
  * `shadow::AbstractShadow`: 密な、因子化された、または浅いシャドウオブジェクト。

# 戻り値

スカラーとしての期待値。

# 例

```julia
val = get_expect_shadow(O, shadow)
```
