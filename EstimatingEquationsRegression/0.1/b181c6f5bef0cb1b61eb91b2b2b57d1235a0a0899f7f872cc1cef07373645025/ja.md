```
predict(m::AbstractGEE; type=:linear)
```

適合したモデルから適合値を返します。typeが:linearの場合は線形予測子を返し、typeが:responseの場合は適合した平均を返します。
