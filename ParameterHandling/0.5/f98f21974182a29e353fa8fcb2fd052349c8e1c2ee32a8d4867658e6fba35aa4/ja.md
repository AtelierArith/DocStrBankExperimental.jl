```
positive(val::Real, transform=exp, ε=sqrt(eps(typeof(val))))
```

`Positive`を返します。`Positive`の`value`は正であることが制約された`Real`数です。これは、`unconstrained_value`を正の実数にマッピングする`transform`の観点から表現されます。`val ≈ transform(unconstrained_value)`を満たします。
