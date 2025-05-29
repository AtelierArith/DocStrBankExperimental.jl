```
NonlinearContact{T,N} <: Contact{T,N}

contact object for impact and friction with a nonlinear friction cone

friction_coefficient: value of friction coefficient
contact_tangent: mapping from world frame to surface tangent frame 
contact_normal: inverse/complement of contact_tangent
contact_origin: position of contact on Body relative to center of mass 
contact radius: radius of contact
```
