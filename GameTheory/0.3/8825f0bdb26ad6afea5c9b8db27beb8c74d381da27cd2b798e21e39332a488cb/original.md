```
NormalFormGame{N,T}
```

Type representing an N-player normal form game.

# Fields

  * `players::NTuple{N,Player{N,T<:Real}}` : Tuple of Player instances.
  * `nums_actions::NTuple{N,Int}` : Tuple of the numbers of actions, one for each player.
