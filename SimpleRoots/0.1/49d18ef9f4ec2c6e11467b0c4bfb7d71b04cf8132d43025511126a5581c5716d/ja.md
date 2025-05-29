```
findzero(f, method::Brent, atol, maxiter)
findzero(f, method::Brent; atol=1e-7, max_iter=100)
```

Brent法を使用して根を見つけます。見つかった値と、許容範囲内で根が見つかったかどうかを指定するBoolのタプルを返します。
