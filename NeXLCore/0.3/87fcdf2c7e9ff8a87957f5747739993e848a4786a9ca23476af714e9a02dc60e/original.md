```
coated_particle(mat::Material, radius::Float64, coating::Material, thickness::Float64, substrate::Union{Nothing,Material} = nothing)
```

Construct a coated particle on an optional substrate.

This model is a good example of how more complex models are constructed.  Use `dump(..)` to display the structure.  You'll notice that the chamber serves as the root `Region`.  The `coating` and `substrate` are in the chamber (children of the chamber `Region`).  The `particle` is a child of the `coating` `Region` because the particle is fully enclosed by the coating.  An electron inside of the coating will enter the particle and leave the coating as soon as it enters the volume representing the particle.  The electron only appears to be within the child-most region at any point in space.  So a typical trajectory might start in the chamber, enter the coating, traverse the thickness of the coating and then enter the particle.  It may eventually leave the particle and reenter the coating, exit the coating and reenter the chamber and finally come to rest in the substrate.
