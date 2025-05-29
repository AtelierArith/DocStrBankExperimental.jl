```
Spinorbit
```

Type for specification of *atomic Spinorbitals* with fields:

  * `.name`: spinorbital name (string)
  * `.n`:  principal quantum number
  * `.n′`:  radial quantum number (number of nodes in radial wavefunction)
  * `.ℓ`:  orbital angular momentum valence electron
  * `.mℓ`:  orbital angular momentum projection valence electron
  * `.ms`: spin magnetic quantum number (Rational{Int})

The type `Spinorbit` is best created with the function `castSpinorbit`.
