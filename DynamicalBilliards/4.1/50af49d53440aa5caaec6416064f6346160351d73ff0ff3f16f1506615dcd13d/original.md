```
randominside(bd::Billiard [, ω]) → p
```

Return a particle `p` with random allowed initial conditions inside the given billiard. If supplied with a second argument the type of the returned particle is `MagneticParticle`, with angular velocity `ω`.

**WARNING** : `randominside` works for any **convex** billiard but it does not work for non-convex billiards. (this is because it uses `distance`)
