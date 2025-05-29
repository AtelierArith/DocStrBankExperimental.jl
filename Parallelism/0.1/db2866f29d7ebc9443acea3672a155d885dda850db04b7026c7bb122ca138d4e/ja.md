```
robust_pmap(f::Function, xs::Any, num_retries::Int=3)
```

一般的なネットワークエラーに対するリトライ機能を持つpmap関数です。
