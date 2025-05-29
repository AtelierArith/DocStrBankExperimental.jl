```
RepeatedGame{N,T}
```

Type representing an N-player repeated game.

# Fields

  * `sg::NormalFormGame{N, T}` : The stage game used to create the repeated game.
  * `delta::Float64` : The common discount rate at which all players discount the future.
