```
slice(F::System, L::LinearSubspace; compile = mixed)
slice(F::AbstractSystem, L::LinearSubspace)
```

多項式系 `F` のゼロ集合を、$Ax = b$ で定義されたアフィン線形部分空間 `L` でスライスします。これにより、システム `[F(x); A x - b] = 0` が構築されます。詳細は [`SlicedSystem`](@ref) を参照してください。
