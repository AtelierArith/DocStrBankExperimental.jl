```
find_main_equation(model, var)
```

パターン `var[t] = __` に一致する最初の方程式の名前を返します。そのような方程式が存在しない場合は、式のどこかに `var[t]` を含む最初の方程式の名前を返します。それも存在しない場合は、`nothing` を返します。
