```julia
register_LorentzVectorLike(T)

```

Function to register a custom type as a LorentzVectorLike.

Ensure the passed custom type has implemented at least the function `getT, getX, getY, getZ` and enables getter functions of the lorentz vector library for the given type. If additionally the functions `setT!, setX!, setY!, setZ!` are implemened for the passed custom type, also the setter functions of the Lorentz vector interface are enabled.
