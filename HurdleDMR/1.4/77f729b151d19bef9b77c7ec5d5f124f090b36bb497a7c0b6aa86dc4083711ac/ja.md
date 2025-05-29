```
coef(m::HDMRCoefs)
```

HDMRを使用してフィットした係数行列を、フィット中に選択されたセグメント（デフォルトではMinAICc）を使用して返します。

# 例:

```julia
  m = fit(HDMR,covars,counts)
  coefspos, coefszero = coef(m)
```
