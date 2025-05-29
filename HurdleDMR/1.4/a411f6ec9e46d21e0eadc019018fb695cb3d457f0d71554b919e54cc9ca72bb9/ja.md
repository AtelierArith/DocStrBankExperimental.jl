```
coef(m::Hurdle; select=MinAICc())
```

適合したTwoPartModelの係数行列の選択されたセグメントを返します。

# 例:

```julia
  m = fit(Hurdle,GeneralizedLinearModel,X,y; Xpos=Xpos)
  coefspos, coefszero = coef(m)
```

# キーワード

  * `kwargs...` は、2つのモデル部分に対する2つのcoef()呼び出しに渡されます。
