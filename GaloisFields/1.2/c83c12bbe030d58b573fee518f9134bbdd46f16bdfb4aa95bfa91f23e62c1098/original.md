```
F = @GaloisField 3
F = @GaloisField ℤ/3ℤ
F = @GaloisField 𝔽₃
F,α = @GaloisField 3^2
```

Different ways of defining a finite field.

For defining a Galois field of prime power order with $n>1$, consider using `@GaloisField!` instead, which allows specifying the display name of the generator.
