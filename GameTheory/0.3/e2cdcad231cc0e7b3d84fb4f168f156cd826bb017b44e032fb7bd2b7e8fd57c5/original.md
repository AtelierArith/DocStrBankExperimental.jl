```
FictitiousPlay{N, T, TG}
```

Type representing a fictitious play model with N players.

# Fields

  * `players::NTuple{N,Player{N,T}}` : Tuple of `Player` instances.
  * `nums_actions::NTuple{N,Int}` : Tuple of the numbers of actions, one for each player.
  * `gain::TG<:AbstractGain` : Gain type.
