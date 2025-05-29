```
const F = GaloisField(p)
const F,α = GaloisField(p, :β => [1, 0, 1])
const F,α = GaloisField(p, n, :β)
```

Return a type representing a finite field.

The single-argument signature returns the finite field $ℤ/pℤ$.

The two-arguments signature returns an algebraic extension of that field, with minimum polynomial given by the second argument: a dense representation of the univariate, monic polynomial, with ascending degree.

The three-arguments signature returns an algebraic extension of that field, with minimum polynomial equal to the [Conway polynomial](https://en.wikipedia.org/wiki/Conway_polynomial_(finite_fields))  for $(p,n)$. The `GaloisFields` package ships with a database of Conway  polynomials and will raise an error if it does not contain an entry for  $(p,n)$.

Note that in the latter two cases, the variable name (e.g. β above) is part of the type. This lets you define identifications between isomorphic (sub)fields. For example, with the following definition

```
const F = @GaloisField! 𝔽₂ β^2 + β + 1
const G = @GaloisField! 𝔽₂ γ^2 + γ + 1
```

the fields $F$ and $G$ are isomorphic, but not canonically. We might define

```
@GaloisFields.identify β => γ + 1
@GaloisFields.identify γ => β + 1
```

to allow for conversions like

```
G(β)
convert(F, γ + 1)
```

In the Conway case, you do not have to define your own identifications, as the Conway polynomials satisfy compatibility relations that allow us to use certain distinguished inclusions between them.
