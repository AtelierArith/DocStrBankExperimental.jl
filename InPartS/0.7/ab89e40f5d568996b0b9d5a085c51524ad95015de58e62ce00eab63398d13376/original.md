```
AbstractParticle{N}
```

Abstract supertype for N-dimensional particle models.

Subtypes of AbstractParticle should be mutable structs. The core functions generally avoid accesing particle properties with one prominent exception: `centerpos` should be a N-dimensional StaticVector of floats and contain a canonical position coordinate for the particle, e.g. the position of the center of mass.
