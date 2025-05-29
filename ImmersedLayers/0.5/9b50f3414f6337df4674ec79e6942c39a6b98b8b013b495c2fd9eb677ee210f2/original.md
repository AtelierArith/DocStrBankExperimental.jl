```
surface_velocity_in_translating_frame!(vel,x,base_cache,motions,t)
```

Evaluates the surface velocity when the problem is set up in a moving frame of reference (specified with the `reference_body` keyword). It removes the translational velocity of the reference body, since this is applied as a free stream velocity (with change of sign).
