```
wigner6j(T::Type{<:Real} = RationalRoot{BigInt}, j₁, j₂, j₃, j₄, j₅, j₆) -> ::T
```

Compute the value of the Wigner-6j symbol     *⎧ j₁  j₂  j₃ ⎫*      ⎩ j₄  j₅  j₆ ⎭ as a type `T` real number. By default, `T = RationalRoot{BigInt}`.

Returns `zero(T)` if any of triangle conditions `δ(j₁, j₂, j₃)`, `δ(j₁, j₆, j₅)`, `δ(j₂, j₄, j₆)`, `δ(j₃, j₄, j₅)` are not satisfied, but throws a `DomainError` if the `jᵢ`s are not integer or halfinteger.
