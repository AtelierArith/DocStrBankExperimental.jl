```julia
elongate(k, ℓ)

```

Transform a distribution on `x` to $y = (1 + ‖x‖²)ᵏ⋅x$ where $‖ ‖$ is the Euclidean norm and `k` is a real number. `k > 0` values make the tails heavier.
