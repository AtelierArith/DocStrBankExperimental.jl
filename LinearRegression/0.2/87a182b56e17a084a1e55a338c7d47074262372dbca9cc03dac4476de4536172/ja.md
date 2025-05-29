```
SolveCholesky()
```

`linregress`(@ref) に `method` として渡すことで、線形回帰システムを解くためにコレスキー分解を使用します。条件が悪いシステムに対しては [`SolveQR`](@ref) よりも速いですが、精度は低くなります。
