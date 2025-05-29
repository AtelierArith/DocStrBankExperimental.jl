```
curve_scalar_type(::Type{<:EllipticCurve})
```

型 [`EllipticCurve`](@ref) のオブジェクトに関連付けられたスカラーの型を返します。この型のオブジェクトに対するすべての操作は、曲線の順序をモジュロで行われます。

この型のオブジェクトは `zero()`, `iszero()`, `one()`, `rand()`, `+`, `-`, `==`, `*`（スカラー型またはポイント型による）、`iseven()`, `isodd()`, `>>`, `inv()`, `divrem()`, `trailing_zeros()`, `DarkIntegers.num_bits()` をサポートしています。
