FFTW plans to be used by all functions in **Fourier Analysis** are incapsulated in this structure. This is the only *operator object* created by this package, all others being *data objects*.

Spectral and cross-spectral computations (frequency domain objects) need only a forward plan (real FFT), while objects based on the analytic signal (time-frequency domain objects) need both a forward (`.p`) and a backward (`.ip`) plan (complex iFFT).

Argument `flags` must be one of the constants here above. Basic usage of the flags involves a trade-off between the time needed to compute the planner and the efficacy for computing the FFTs. The following flags are sorted in ascending order of time needed to be computed and efficacy: `plan_estimate`, `plan_measure`, `plan_patient`, `plan_exhaustive`. By default *FourierAnalysis* adopts `plan_estimate`, which allows the quickest search, but the least optimal choice. Other flags may be worth if several FFT computations are to be done with the same setting. See [here](http://www.fftw.org/fftw3_doc/Planner-Flags.html) for details.

Argument `timelimit` is the maximum time (in seconds) allowed to FFTW for optimizing the plans. Setting this to `-1.0` amounts to imposing no time limits.

FFTW plans are computed for a given window length `wl` and data type `type`.

`Planners` objects may be passed as an argument to constructors of [FDobjects](@ref) and [TFobjects](@ref) by using one of the `Planner` constuctor here below.

**Constructors**

```julia
Planner(flags :: UInt32,
    timelimit :: Union{Int, Float64},
           wl :: Int,
         type :: Type,
           bw :: Bool = false)
```

Use this to create a Planner object, passing as argument a FFTW `flags` constant and `timelimit`, the window length `wl` and the type of the input data `type`, which must be real, e.g., Float64.

If `bw` is false (default), a dummy backward plan is created, otherwise a backward plan is created for the complex data type corresponding to `type` (e.g., if `type` is Float64, it will created for ComplexF64 data.)

For example, suppose 𝐗 is a vector of many matrices of multivariate time-series sampled at 128 samples per second and that we want to compute the spectra for all of them using a 256-point FFT. We first create a plan by

```julia
p=Planner(plan_exhaustive, 10.0, 256, eltype(𝐗[1]))
```

Then we invoke the [Spectra](@ref) function passing the plan as argument:

```julia
𝐒=spectra(𝐗, sr, t; planner=p)
```

A shorter construction syntax is available when only the forward plan is needed and the type of the data is Float64:

```julia
Planner(flags :: UInt32,
    timelimit :: Union{Int, Float64},
           wl :: Int)
```

For example, the line above could have been written more shortly as

```julia
p=Planner(plan_exhaustive, 10.0, 256)
```

In order to create also a backward plan you would use instead

```julia
p=Planner(plan_exhaustive, 10.0, 256, eltype(𝐗[1]), true)
```
