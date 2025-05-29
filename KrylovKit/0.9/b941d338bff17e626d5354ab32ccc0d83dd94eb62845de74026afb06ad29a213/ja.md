```
shrink!(fact::KrylovFactorization, k)
```

既存のKrylov因子分解`fact`を長さ`k`に縮小します。`length(fact)<=k`の場合は何もしません。
