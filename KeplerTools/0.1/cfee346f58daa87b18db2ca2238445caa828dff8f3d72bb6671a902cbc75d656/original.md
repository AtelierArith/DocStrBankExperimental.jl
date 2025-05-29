```
torb = p_lambert_velocity(sorbₛ, eorb, stime, etime, μ, s_patch_position=@SVector(zeros(3)), e_patch_position=@SVector(zeros(3)); kwargs...)
```

Computes the single-revolution orbit around a body with gravity parameter `μ`, passing through the positions of orbits  `sorb` and `eorb` at times `stime` and `etime`, respectively.

Positions `s_patch_position` and `e_patch_position` can be provided to modify the start and end positions, respectively. This can be used to minimize patching error across spheres of influence.
