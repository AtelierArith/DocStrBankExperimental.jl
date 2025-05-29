```
squad(Rin, tin, tout; [kwargs...])
```

"Spherical QUADrangle interpolation" of the input `Rotor`s `Rin` with corresponding times `tin`, to the output times `tout`.

This is a slightly generalized version of [Shoemake's "spherical Bézier curves"](https://doi.org/10.1145/325165.325242), to allow for time steps of varying sizes.

The input `Rin` and `tin` must be vectors of the same length.  The output `tout` may be either a single real number or a vector of real numbers.  Both `tin` and `tout` are assumed to be sorted, and `tout` is assumed to be contained entirely within `tin`; no extrapolation will be done.

See also [`squad!`](@ref) for in-place versions of this function.

# Keyword arguments

If `unflip=true` is passed as a keyword, the [`unflip`](@ref) function will be applied to `Rin`.

If `validate=true` is passed as a keyword, the time ordering of the input `tin` and `tout` will be tested to ensure that no extrapolation will be done.

If `compute_angular_velocity=true` is passed as a keyword, the return value will be a tuple.  The first element of the tuple will be a vector of `Rotor`s as before, but the second element will be a vector of `QuatVec`s representing the angular velocity.

If `compute_derivative=true` is passed as a keyword, the return value will be a tuple.  The first element of the tuple will be a vector of `Rotor`s as before, but the last element will be a vector of `Quaternion`s representing the time-derivative of the rotors.  Note that if `compute_angular_velocity=true`, this tuple will have three elements.
