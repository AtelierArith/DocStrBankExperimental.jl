```
FFTAutocovMethod <: AbstractAutocovMethod
```

The `FFTAutocovMethod` uses a standard algorithm for estimating the mean autocovariance of MCMC chains.

The algorithm is the same as the one of [`AutocovMethod`](@ref) but this method uses fast Fourier transforms (FFTs) for estimating the autocorrelation.

!!! info
    To be able to use this method, you have to load a package that implements the [AbstractFFTs.jl](https://github.com/JuliaMath/AbstractFFTs.jl) interface such as [FFTW.jl](https://github.com/JuliaMath/FFTW.jl) or [FastTransforms.jl](https://github.com/JuliaApproximation/FastTransforms.jl).

