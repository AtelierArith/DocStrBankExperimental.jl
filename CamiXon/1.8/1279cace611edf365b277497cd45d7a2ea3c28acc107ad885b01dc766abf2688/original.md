```
Shells(name, shells)
```

Type for specification of closed electron [`Shells`](@ref) with fields:

  * `.name`: shell configuration (`::String`)
  * `.count`: number of shells (`::Int`)
  * `.n`: array of shell principal quantum numers (`Vector{Int}`)
  * `.ℓ`: array of shell angular momenta (`::Vector{Int}`)
  * `.shell`: Array of Shells (`::Vector{Shell}`)

The type `Shells` is best created with the function `castShells`.
