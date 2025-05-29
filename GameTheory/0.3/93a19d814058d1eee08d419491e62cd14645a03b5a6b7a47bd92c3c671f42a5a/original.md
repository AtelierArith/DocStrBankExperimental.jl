```
NormalFormGame(players...)
```

Constructor of an N-player NormalFormGame with N Player instances.

# Arguments

  * `players::Player{N,T}...` : N Player instances

# Examples

```julia
# p1, p2, and p3 are all of type `Player{3,T}` for some `T`
NormalFormGame(p1, p2, p3)
```
