```
ispinned(p::MagneticParticle, bd::Billiard)
```

Return `true` if the particle is pinned with respect to the billiard. Pinned particles either have no valid collisions (go in circles forever) or all their valid collisions are with periodic walls, which again means that they go in cirles for ever.
