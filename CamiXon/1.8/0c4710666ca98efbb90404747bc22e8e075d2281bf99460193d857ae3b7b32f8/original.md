```
Term(name::String, n::Int, ℓ::Int, S::Real, L::Int, J::Real)
```

Type for specification of atomic *fine-structure Terms* with fields:

  * `name`: name
  * `.n`:  principal quantum number
  * `.n′`:  radial quantum number (number of nodes in wavefunction)
  * `.ℓ`:  orbital angular momentum valence electron
  * `.S`:  total electron spin in units of ħ
  * `.L`:  total orbital angular momentum in units of ħ
  * `.J`:  total electronic angular momentum in units of ħ

The type `Term` is best created with the function `castTerm`.
