```
ẋ = dynamics(model, z::AbstractKnotPoint)
ẋ = dynamics(model, x, u, [t=0])
```

強制された動的の連続ダイナミクスを、状態 `x`、制御 `u`、および時間 `t`（オプション）を用いて計算します。
