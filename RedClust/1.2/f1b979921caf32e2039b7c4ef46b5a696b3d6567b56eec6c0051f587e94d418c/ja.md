```
binderloss(a::ClustLabelVector, b::ClustLabelVector;
normalised = true) -> Float64
```

2つのクラスタリング間のバインダー損失を計算します。`normalised = true` の場合、結果は `a` と `b` の間のランダムインデックスの1引きに等しくなります。
