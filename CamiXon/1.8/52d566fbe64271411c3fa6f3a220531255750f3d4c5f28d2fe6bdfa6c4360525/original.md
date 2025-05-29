```
castShells(strShells::String; msg=false)
```

Create configuration of closed electron [`Shells`](@ref) with fields:

  * `.name`: shell configuration (`::String`)
  * `.count`: number of shells (`::Int`)
  * `.n`: array of shell principal quantum numers (`Vector{Int}`)
  * `.ℓ`: array of shell angular momenta (`::Vector{Int}`)
  * `.shell`: Array of Shells (`::Vector{Shell}`)

#### Example:

```
julia> castShells("1s2s",msg=true);
Shell: 1s²
    number of shell electrons: N = 2
    principal quantum number: n = 1
    orbital angular momentum of electrons: ℓ = 0
Shell: 2s²
    number of shell electrons: N = 2
    principal quantum number: n = 2
    orbital angular momentum of electrons: ℓ = 0
```
