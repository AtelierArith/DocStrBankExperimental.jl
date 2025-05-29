```
score!(v::mIHTVariable)
```

多変量ガウスモデルのために勾配 `Γ(Y - XB)X'` を計算します。残差は solve_Σ! で更新されました。
