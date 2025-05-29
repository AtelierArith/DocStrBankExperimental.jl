```
sample!(F::SampledSystem; path_ids=Vector(1:nsolutions(F)), n_instances=1) -> SampledSystem
```

[`solve`](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/solve/) メソッドを使用して、`path_ids` で定義された id を持つ多項式系 `F` の解を `n_instances` のランダムパラメータに追跡します。
