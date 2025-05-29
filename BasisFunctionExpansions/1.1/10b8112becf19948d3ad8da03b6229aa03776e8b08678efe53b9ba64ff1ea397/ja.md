```
y,A = getARregressor(y::AbstractVector,na::Integer)
```

短縮された出力信号 `y` と回帰子行列 `A` を返します。ここで、最小二乗ARモデルの次数 `na` の推定は `y\A` です。
