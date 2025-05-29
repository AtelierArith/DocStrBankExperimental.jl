```
project(M::Circle, p, X)
```

Project a value `X` onto the tangent space of the point `p` on the [`Circle`](@ref) `M`.

For the real-valued case this is just the identity. For the complex valued case `X` is projected onto the line in the complex plane that is parallel to the tangent to `p` on the unit circle and contains `0`.
