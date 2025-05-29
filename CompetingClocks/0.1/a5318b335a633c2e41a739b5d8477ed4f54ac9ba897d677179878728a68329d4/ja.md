```
next(sampler, when, rng)
```

サンプラーに次に何が起こるかを尋ねます。形式は `(when, which)::Tuple{TimeType,KeyType}` です。`rng` は乱数生成器です。
