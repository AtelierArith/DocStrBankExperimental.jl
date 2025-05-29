```
clebschgordan(T::Type{<:Real} = RationalRoot{BigInt}, j₁, m₁, j₂, m₂, j₃, m₃ = m₁+m₂) -> ::T
```

Compute the value of the Clebsch-Gordan coefficient <j₁, m₁; j₂, m₂ | j₃, m₃ > as a type `T` real number. By default, `T = RationalRoot{BigInt}` and `m₃ = m₁+m₂`.

Returns `zero(T)` if the triangle condition `δ(j₁, j₂, j₃)` is not satisfied, but throws a `DomainError` if the `jᵢ`s and `mᵢ`s are not (half)integer or `abs(mᵢ) > jᵢ`.
