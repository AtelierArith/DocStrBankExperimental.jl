```
ll, e = update!(f::AbstractFilter, u, y, p = parameters(f), t = index(f))
```

`predict!` と `correct!` の1ステップを実行し、対数尤度と予測誤差を返します。
