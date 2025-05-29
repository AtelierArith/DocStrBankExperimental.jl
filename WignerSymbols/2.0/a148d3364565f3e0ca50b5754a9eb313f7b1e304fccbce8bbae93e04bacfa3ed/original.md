```
racahW(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, J, j₃, J₁₂, J₂₃) -> ::T
```

Compute the value of Racah's W coefficient `W(j₁, j₂, J, j₃; J₁₂, J₂₃) = <(j₁,(j₂j₃)J₂₃)J | ((j₁j₂)J₁₂,j₃)J> / sqrt((2J₁₂+1)*(2J₁₃+1))` as a type `T` real number. By default, `T = RationalRoot{BigInt}`.

Returns `zero(T)` if any of triangle conditions `δ(j₁, j₂, J₁₂)`, `δ(j₂, j₃, J₂₃)`, `δ(j₁, J₂₃, J)`, `δ(J₁₂, j₃, J)` are not satisfied, but throws a `DomainError` if the `jᵢ`s and `J`s are not integer or halfinteger.
