# 拡張ヘルプ

```
difference(X::AbstractHyperrectangle, Y::AbstractHyperrectangle)
```

### 出力

ハイパーレクタングルの和集合からなる `UnionSetArray`。この和集合は一般に凸ではないことに注意してください。

### アルゴリズム

この実装は `IntervalArithmetic.setdiff` を使用しています。
