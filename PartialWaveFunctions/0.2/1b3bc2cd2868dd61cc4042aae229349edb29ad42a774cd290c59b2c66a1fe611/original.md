```
wignerD(j, m1, m2, α, cosβ, γ)
```

Wigner D-function for representation `j` with indices `m1`, `m2`, α, β, and γ are the rotation angles The function gives the value of the matrix element

```
    ⟨ j m1 | exp(-i Jz α) exp(-i Jy β) exp(-i Jz γ) | j m2 ⟩.
```

The input values are expected to be **integers**. For a general case including half-integers see `wignerD_doublearg`.
