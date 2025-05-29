```
sminreal(sys)
```

Compute the structurally minimal realization of the state-space system `sys`. A structurally minimal realization is one where only states that can be determined to be uncontrollable and unobservable based on the location of 0s in `sys` are removed.

Systems with numerical noise in the coefficients, e.g., noise on the order of `eps` require truncation to zero to be affected by structural simplification, e.g.,

```julia
trunc_zero!(A) = A[abs.(A) .< 10eps(maximum(abs, A))] .= 0
trunc_zero!(sys.A); trunc_zero!(sys.B); trunc_zero!(sys.C)
sminreal(sys)
```

In contrast to [`minreal`](@ref), which performs pole-zero cancellation using linear-algebra operations, has an 𝑂(nₓ^3) complexity and is subject to numerical tolerances, `sminreal` is computationally very cheap and numerically exact (operates on integers). However, the ability of `sminreal` to reduce the order of the model is much less powerful.

See also [`minreal`](@ref).
