```
optimize(F::System)
```

与えられたシステム `F` の評価コストを最適化します。これは、与えられた式に対して多変数ホーナー法則を適用します。詳細は [`horner`](@ref) を参照してください。

### 例

```julia
julia> f
System of length 4
 4 variables: z₁, z₂, z₃, z₄

 z₁ + z₂ + z₃ + z₄
 z₂*z₁ + z₂*z₃ + z₃*z₄ + z₄*z₁
 z₂*z₃*z₁ + z₂*z₃*z₄ + z₂*z₄*z₁ + z₃*z₄*z₁
 -1 + z₂*z₃*z₄*z₁

julia> optimize(f)
System of length 4
 4 variables: z₁, z₂, z₃, z₄

 z₁ + z₂ + z₃ + z₄
 (z₂ + z₄)*z₁ + (z₂ + z₄)*z₃
 z₁*(z₃*z₄ + (z₃ + z₄)*z₂) + z₂*z₃*z₄
 -1 + z₂*z₃*z₄*z₁
```
