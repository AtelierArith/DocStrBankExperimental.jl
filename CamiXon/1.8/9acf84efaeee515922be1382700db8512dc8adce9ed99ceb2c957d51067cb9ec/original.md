```
Orbit(name, n, n′, ℓ, mℓ)
```

Type for specification of *atomic orbitals* with fields:

  * `.name`: name
  * `.n`:  principal quantum number
  * `.n′`:  radial quantum number (number of nodes in radial wavefunction)
  * `.ℓ`:  orbital angular momentum valence electron
  * `.mℓ`:  orbital angular momentum projection valence electron

The type `Orbit` is best created with the function `castOrbit`.
