```
coef(m::DMRCoefs)
```

DMRでフィットした係数行列を、フィット中に選択されたセグメント（デフォルトではMinAICc）を使用して返します。

# 例:

```julia
  m = fit(DMR,covars,counts)
  coef(m)
```
