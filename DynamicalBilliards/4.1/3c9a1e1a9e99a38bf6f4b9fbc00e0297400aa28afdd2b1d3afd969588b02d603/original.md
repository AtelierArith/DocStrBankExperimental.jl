```
propagate!(p::AbstractParticle, t)
```

Propagate the particle `p` for given time `t`, changing appropriately the the `p.pos` and `p.vel` fields.

```
propagate!(p, position, t)
```

Do the same, but take advantage of the already calculated `position` that the particle should end up at.
