```
KL(p::Distribution, q::Distribution) -> T
KL(p::Distribution, q::Distribution, n_samples::Int) -> T
```

KL(p||q)のKLダイバージェンスを、サンプリングまたは解析的に返します。
