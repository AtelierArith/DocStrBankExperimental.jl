# 拡張ヘルプ

```
linear_map(M::AbstractMatrix, Z::AbstractZonotope)
```

### 出力

`Zonotope`。

### アルゴリズム

中心と生成器に線形写像を適用します。

出力次元が1の場合、特化したアルゴリズムにより、結果のゾノトープは単一の生成器のみを持つことが保証されます。
