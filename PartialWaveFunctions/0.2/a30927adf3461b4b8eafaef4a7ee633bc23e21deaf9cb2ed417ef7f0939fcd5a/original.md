```
wignerd(j, m1, m2, cosβ)
```

Small wigner d-function for representation `j` with indices `m1`, `m2`, the argument `cosβ` is the cosine of the rotation angle. The function gives the value of the matrix element

```
    ⟨ j m1 | exp(-i Jy β)| j m2 ⟩.
```

The input values are expected to be **integers**. For a general case including half-integers see `wignerd_doublearg`.
