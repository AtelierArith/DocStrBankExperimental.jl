```
Player{T} <: AbstractPlayer
```

A Go Fish player object where `T` is the player id type.

# Fields

  * `id::Int`: suit of card
  * `cards::Vector{Card}`: player's cards
