```julia
FFTOperator(A) -> F
```

yields an FFT operator suitable for computing the fast Fourier transform of arrays similar to `A`.  The operator can also be specified by the real/complex floating-point type of the elements of the arrays to transform and their dimensions:

```julia
FFTOperator(T, dims) -> F
```

where `T` is one of `Float64`, `Float32` (for a real-complex FFT), `Complex{Float64}`, `Complex{Float32}` (for a complex-complex FFT) and `dims` gives the dimensions of the arrays to transform (by the `Direct` or `InverseAdjoint` operation).

The interest of creating such an operator is that it caches the ressources necessary for fast computation of the FFT and can be therefore *much* faster than calling `fft`, `rfft`, `ifft`, etc.  This is especially true on small arrays.  Keywords `flags` and `timelimit` may be used to specify planning options and time limit to create the FFT plans (see http://www.fftw.org/doc/Planner-Flags.html).  The defaults are `flags=FFTW.MEASURE` and no time limit.

An instance of `FFTOperator` is a linear mapping which can be used as any other mapping:

```julia
F*x     # yields the FFT of x
F'*x    # yields the adjoint FFT applied to x, that is the backward FFT of x
F\x     # yields the inverse FFT of x
```

See also: [`fft`](@ref), [`plan_fft`](@ref), [`bfft`](@ref),           [`plan_bfft`](@ref), [`rfft`](@ref), [`plan_rfft`](@ref),           [`brfft`](@ref), [`plan_brfft`](@ref).
