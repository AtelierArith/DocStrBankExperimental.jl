```
S(p::Union{Particle, PDGID, Integer})
```

Returns the spin S.

This is valid for mesons only. `nothing` is returned otherwise. Mesons with PDGIDs of the kind 9XXXXXX (N=9) are not experimentally well-known particles and `nothing` is returned too.
