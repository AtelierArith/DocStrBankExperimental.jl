```
pitremoval(dem::Matrix{<:Real})
```

中心セルが周囲のセルよりも`limit`低い場合、3x3パッチからDEM配列のくぼみを削除します。
