```
indicator_cochain(R, K, σ)
```

Return the indicator function `f` of the n-simplex `σ` as a [`Cochain`](@ref). That is, a cochain such that `f(σ) = 1` and  `f(τ) = 0` for all other n-simplices of `K`.

Notice that, nevertheless, `f` is still skew-symmetric over permutations of `σ`s indices.

If `Κ` does not contain `σ`, the returned cochain is identically zero.
