```
velocity(sys::AbstractSystem, i)
```

Return a velocity vector if `i::Integer`, a vector of velocities if `i` is a  vector of integers or `:`. Return type should be a vector of vectors each containing `D` elements that are `<:Unitful.Velocity`. Returned value of the function may be `missing`.
