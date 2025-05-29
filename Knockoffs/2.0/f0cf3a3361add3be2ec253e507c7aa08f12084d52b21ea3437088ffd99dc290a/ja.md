```
update_normalizing_constants!(Q::AbstractMatrix{T}, q::AbstractVector{T})
```

方程式 (5) を使用して正規化定数を再帰的に計算します。

# 入力

  * `Q`: `K × K × p` 配列。`Q[:, :, j]` は `j` 番目の状態の遷移確率の `K × K` 行列、すなわち Q[l, k, j] = P(X*{j} = k | X*{j - 1} = l) です。最初の遷移行列は使用されません。
  * `q`: 初期確率の `K × 1` ベクトル

# todo: 効率性
