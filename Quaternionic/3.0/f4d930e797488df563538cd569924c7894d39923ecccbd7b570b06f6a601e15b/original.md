```
slerp(q₁, q₂, τ; [unflip=false])
```

"Spherical Linear intERPolation" of a pair of quaternions.

The result of a "slerp" is given by

```
    (q₂ / q₁)^τ * q₁
```

When `τ` is 0, this evaluates to `q₁`; when `τ` is 1, this evaluates to `q₂`; for any other values the result varies between the two.

Note that applying this to successive pairs of quaternions as in `slerp(q₁, q₂, τₐ)` and `slerp(q₂, q₃, τᵦ)` will be continuous, but the derivative will be discontinuous when moving from the first pair to the second.  See [`squad`](@ref) for a more continuous curve.

If `unflip=true` is passed as a keyword, and the input quaternions are more anti-parallel than parallel, the sign of `q₂` will be flipped before the result is computed.

See also [`slerp∂slerp∂τ`](@ref), to simultaneously evaluate this function and its derivative with respect to `τ`, or [`slerp∂slerp`](@ref) to evaluate this function and its derivative with respect to each parameter of the input.
