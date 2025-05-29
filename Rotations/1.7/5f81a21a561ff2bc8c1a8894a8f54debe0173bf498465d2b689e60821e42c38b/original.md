```
QuatRotation{T} <: Rotation
```

4-parameter attitute representation that is singularity-free. Quaternions with unit norm represent a double-cover of SO(3). The `QuatRotation` does NOT strictly enforce the unit norm constraint, but certain methods will assume you have a unit quaternion. Follows the Hamilton convention for quaternions.

# Constructors

```julia
QuatRotation(w,x,y,z)
QuatRotation(q::AbstractVector)
```

where `w` is the scalar (real) part, `x`, `y`, and `z` are the vector (imaginary) part, and `q = [w,x,y,z]`.
