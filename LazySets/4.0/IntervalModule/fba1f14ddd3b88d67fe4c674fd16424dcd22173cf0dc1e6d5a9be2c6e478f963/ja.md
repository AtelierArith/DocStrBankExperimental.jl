# 拡張ヘルプ

```
linear_map(M::AbstractMatrix, x::Interval)
```

### 出力

`M`の先頭次元（すなわち行数）に応じて、間隔またはゾノトープのいずれかになります：

  * `size(M, 1) == 1` の場合、出力は行列 `M` によってスケーリングされた `x` から得られる `Interval` です。
  * `size(M, 1) ≠ 1` の場合、出力は中心 `M * center(x)` と単一の生成子 `M * g` を持つ `Zonotope` です。ここで、`g = (high(x)-low(x))/2` です。
