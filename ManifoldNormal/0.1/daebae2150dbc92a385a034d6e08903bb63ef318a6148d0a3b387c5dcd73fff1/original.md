```
adjoint_noise(noise::ActionNoise{<:GroupOperationAction})
```

If the noise is defined by a group operation action, compute the corresponding noise for the action with switched sides. It is based on the identities

$$
χ \exp(ξ) = \exp(χ ξ χ^{-1}) χ
$$

and

$$
\exp(ξ) χ = χ \exp(χ^{-1} ξ χ)
$$
