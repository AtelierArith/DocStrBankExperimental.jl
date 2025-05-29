```
bounce!(p::AbstractParticle, bd::Billiard) → i, t, pos, vel
```

"Bounce" the particle (advance for one collision) in the billiard. Takes care of finite-precision issues.

Return:

  * index of the obstacle that the particle just collided with
  * the time from the previous collision until the current collision `t`
  * position and velocity of the particle at the current collision (*after* the collision has been resolved!). The position is given in the unit cell of periodic billiards. Do `pos += p.current_cell` for the position in real space.

```julia
bounce!(p, bd, raysplit) → i, t, pos, vel
```

Ray-splitting version of `bounce!`.
