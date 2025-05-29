```
Δ(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, j₃) -> ::T
```

Computes the triangle coefficient `Δ(j₁, j₂, j₃) = √((j₁+j₂-j₃)!*(j₁-j₂+j₃)!*(j₂+j₃-j₁)! / (j₁+j₂+j₃+1)!)` as a type `T` real number.

Returns `zero(T)` if the triangle condition `δ(j₁, j₂, j₃)` is not satisfied, but throws a `DomainError` if the `jᵢ`s are not (half)integer
