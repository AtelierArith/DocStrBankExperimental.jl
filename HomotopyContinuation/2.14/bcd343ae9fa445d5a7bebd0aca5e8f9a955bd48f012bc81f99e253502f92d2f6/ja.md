```
SlicedSystem(F::AbstractSystem, L::LinearSubspace)
```

与えられた多項式系 `F` と、$Ax = b$ によって定義されるアフィン線形部分空間 `L` に対して、このシステム `[F(x); A x - b] = 0` を構築します。詳細は [`slice`](@ref) を参照してください。
