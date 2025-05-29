```
support_enumeration(g)
```

Compute mixed-action Nash equilibria with equal support size for a 2-player normal form game by support enumeration. For a non-degenerate game input, these are all the Nash equilibria.

The algorithm checks all the equal-size support pairs; if the players have the same number n of actions, there are 2n choose n minus 1 such pairs. This should thus be used only for small games.

# Arguments

  * `g::NormalFormGame{2,T}`: 2-player NormalFormGame instance.

# Returns

  * `::Vector{NTuple{2,Vector{S}}}`: Mixed-action Nash equilibria that are found, where `S` is Float if `T` is Int or Float, and Rational if `T` is Rational.
