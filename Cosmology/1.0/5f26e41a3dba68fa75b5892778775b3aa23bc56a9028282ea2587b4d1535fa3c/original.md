```
angular_diameter_dist([u::Unitlike,] c::AbstractCosmology, [z₁,] z₂)
```

Ratio of the proper transverse size in Mpc of an object at redshift `z₂` to its angular size in radians, as seen by an observer at `z₁`.  Redshift `z₁` defaults to 0 if omitted.  Will convert to compatible unit `u` if provided.
