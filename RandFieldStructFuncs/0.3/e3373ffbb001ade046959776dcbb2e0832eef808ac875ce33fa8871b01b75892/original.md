```
A = EmpiricalStructFunc{T}(S[, plan])
```

yields an (empty) empirical structure function with values of floating-point type `T` and for a support `S`. Parameter `T` may be omitted to determine the floating-point type from the arguments.

If optional argument `plan` is not specified, the empirical structure function is updated by means of fast Fourier transforms (FFTs) and keywords `flags` and `timelimit` may be specified to build the FFT plan (defaults are `flags=FFTW.ESTIMATE` and `timelimit=Inf`). Otherwise, `plan` maybe a precomputed suitable FFT plan or `nothing` to use a **slow** update method.

The base method `push!` can be used to *update* the data into the empirical structure function object:

```
push!(A, φ)
```

where `φ` is a random sample which can be an array of the same size as `S`. If `plan` is `nothing`, `φ` may also be a vector whose length is the number of non-zeros in the support `S`.

An empirical structure function object `A` has the following properties:

```
A.support # support
A.num     # cumulated numerator
A.den     # denominator
A.nobs    # number of observations
```

The following methods are applicable:

```
nobs(A)         # number of observations
Dᵩ = values(A)  # compute the empirical structure function
valtype(A)      # element type of `Dᵩ`
```

The empirical structure function `Dᵩ` computed by `values(A)` is an `OffsetArray` instance such that:

```
Dᵩ[Δr]
```

yields the value of the empirical structure function for a displacement `Δr` which may be specified as a Cartesian index.
