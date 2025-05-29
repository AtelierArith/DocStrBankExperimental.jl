```
sspin(p::Union{Particle, PDGID, Integer})
```

Returns the spin S as 2S+1.

This is valid for mesons only. `nothing` is returned otherwise. Mesons with PDGIDs of the kind 9XXXXXX (N=9) are not experimentally well-known particles and `nothing` is returned too.
