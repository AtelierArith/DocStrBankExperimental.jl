```
plan_fft(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

Pre-plan an optimized FFT along given dimensions (`dims`) of arrays matching the shape and type of `A`.  (The first two arguments have the same meaning as for [`fft`](@ref).) Returns an object `P` which represents the linear operator computed by the FFT, and which contains all of the information needed to compute `fft(A, dims)` quickly.

To apply `P` to an array `A`, use `P * A`; in general, the syntax for applying plans is much like that of matrices.  (A plan can only be applied to arrays of the same size as the `A` for which the plan was created.)  You can also apply a plan with a preallocated output array `Â` by calling `mul!(Â, plan, A)`.  (For `mul!`, however, the input array `A` must be a complex floating-point array like the output `Â`.) You can compute the inverse-transform plan by `inv(P)` and apply the inverse plan with `P \ Â` (the inverse plan is cached and reused for subsequent calls to `inv` or `\`), and apply the inverse plan to a pre-allocated output array `A` with `ldiv!(A, P, Â)`.

The `flags` argument is a bitwise-or of FFTW planner flags, defaulting to `FFTW.ESTIMATE`. e.g. passing `FFTW.MEASURE` or `FFTW.PATIENT` will instead spend several seconds (or more) benchmarking different possible FFT algorithms and picking the fastest one; see the FFTW manual for more information on planner flags.  The optional `timelimit` argument specifies a rough upper bound on the allowed planning time, in seconds. Passing `FFTW.MEASURE` or `FFTW.PATIENT` may cause the input array `A` to be overwritten with zeros during plan creation.

[`plan_fft!`](@ref) is the same as [`plan_fft`](@ref) but creates a plan that operates in-place on its argument (which must be an array of complex floating-point numbers). [`plan_ifft`](@ref) and so on are similar but produce plans that perform the equivalent of the inverse transforms [`ifft`](@ref) and so on.
