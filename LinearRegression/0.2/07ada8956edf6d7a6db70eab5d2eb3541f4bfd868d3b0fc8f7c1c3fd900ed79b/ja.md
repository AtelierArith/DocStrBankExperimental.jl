```
SolveQR()
```

`linregress`(@ref) に `method` として渡して、QR因子分解を使用して線形回帰システムを解きます。条件が悪いシステムに対しては、[`SolveCholesky`](@ref) よりも遅いですが、より正確です。
