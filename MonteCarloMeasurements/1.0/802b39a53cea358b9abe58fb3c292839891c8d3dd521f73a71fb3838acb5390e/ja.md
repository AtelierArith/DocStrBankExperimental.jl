```
systematic_sample([rng::AbstractRNG,] N, d=Normal(0,1); permute=true)
```

は、分布 `d` から体系的にサンプリングされた長さ `N` の `Vector` を返します。`permute=false` の場合、このベクトルはソートされます。
