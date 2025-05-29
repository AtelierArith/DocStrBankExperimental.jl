### Rotating an affine transform

There are two ways to combine a rotation by angle `θ` (in radians counterclockwise) with an affine transform `A`.  Left-rotating as in:

```julia
B = rotate(θ, A)
```

results in rotating the output of the transform; while right-rotating as in:

```julia
C = rotate(A, θ)
```

results in rotating the input of the transform.  The above examples are similar to:

```julia
B = R∘A
C = A∘R
```

where `R` implements rotation by angle `θ` around `(0,0)`.

See also: [`AffineTransform`](@ref), [`scale`](@ref), [`translate`](@ref).
