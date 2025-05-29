```julia
   (1)
   function analyticsignal( X  :: Union{Vector{T}, Matrix{T}},
                            wl :: Int     = size(X, 1);
                        nonlinear :: Bool    =  false,
                        planner   :: Planner =  getplanner,
                        ⏩       :: Bool    =  true) where T<:Real

   (2)
   function analyticsignal( 𝐗      :: Vector{Matrix{T}},
                            wl     :: Int;
                        nonlinear  ::  Bool      =  false,
                        planner    ::  Planner   =  getplanner,
                        ⏩        ::  Bool      =  true) where T<:Real
```

(1)

Compute the analytic signal(AS) of vector `X` or of all column vectors of matrix `X` via the FFT and iFFT procedure, as explained in Marple(1999). If `wl`=size(X, 1) (default), use the standard method passing to the FFT and iFFT all samples in `X` altogether, whereas if `wl`<size(X, 1) a sliding-windows method is used (see below).

Return the analytic signal `𝑌`, a complex vector if `X` is a vector or a complex matrix holding in its columns the analytic signal of the columns of `X` if `X` is a matrix. `𝑌` has the same number of samples (rows) as `X`.

Contrarely to what is done in the [DSP](https://github.com/JuliaDSP/DSP.jl) package, the DC level of the signal is removed, therefore, if the input signal features a non-zero DC level, the real part of the AS will be equal to the input signal with the DC level removed. The imaginary part of `𝑌` is the Hilbert transform of such no-DC `X`.

The sliding-windows AS allows an efficient estimation of the AS for vectors and matrices when they are very large; it proceeds computing the AS on 50% sliding overlapping windows and forming the AS by retaining the central half of each window. The number of points effectively used to obtain the final estimation is $wl$÷2 (integer division). `wl` must be even for using this estimation. This procedure produces edge effects, thus the first and last $wl÷4$ samples of the AS estimation should be discarded. In practice, one requires the AS of a larger data segment and trims at least $wl÷4$ samples at the beginning and end of the estimation. This is done automatically by the [`TFanalyticsignal`](@ref) function.

Also, the sliding-windows AS method creates small discontinuities at sample $wl$÷4 and then every $wl$÷2 samples, therefore $wl$ should be chosen as large as possible.

!!! note "Nota Bene"
    In order to avoid FFT computation of very long epochs, if `wl` > 2^14, then `wl` is set to 2^10. Below this limit, as long as the computations are feasable, use the standard method. If you absolutely need to use the sliding-windows method, see [window length in FFTW](@ref) for setting efficiently argument `wl`.

    The input signal should be previously band-pass or high-pass filtered so as not to contain frequency components below the first discrete Fourier frequency obtained with windows of `wl` samples, that is, below sr/wl Hz, where sr is the sampling rate.


**Optional Keyword Arguments**:

`nonlinear`, if true, the analytic signal is normalized so that its amplitude is $1.0$ at all points. This allow non-linear univariate and bivariate estimations (see [timefrequencyuni.jl](@ref) and [timefrequencybi.jl](@ref)).

`planner` is an instance of the [`Planner`](@ref) object, holding the forward and backward FFTW plans used to compute the FFTs and the iFFTs. By default the planner is computed, but it can be passed as an argumet here if it is pre-computed. This is interesting if the `analyticsignal` function is to be invoked repeatedly.

if `⏩` is true, the method is run in multi-threaded mode across the series in `X` if the number of series is at least twice the number of threads Julia is instructed to use. See [Threads](@ref).

(2)

Compute the analytic signal for all $k$ multivariate data matrices given as a vector of matrices `𝐗`. Return a vector of matrices hodling the corresponding analytic signals as in method (1). The FFT and iFFT plans are computed only once. The $k$ matrices in `𝐗` may have different number of columns (i.e., different number of series) and different number of rows (samples). However, the number of rows must be larger than `wl` for all of them.

If `⏩` is true, this method run in multi-threaded mode across the matrices in `𝐗` if the number of matrices is at least twice the number of threads Julia is instructed to use, otherwise it tries to run each analytic signal estimation in multi-threaded mode as per method (1). See [Threads](@ref).

This function is called by the following functions operating on time-frequency reprsentations: [`TFanalyticsignal`](@ref), [`TFamplitude`](@ref), [`TFphase`](@ref), [`meanAmplitude`](@ref), [`concentration`](@ref), [`meanDirection`](@ref), [`comodulation`](@ref), [`coherence`](@ref).

**References** Marple S.L. (1999) Computing the Discrete-Time Analytic Signal via FFT. IEEE Transactions on Signal Processing 47(9), 2600-3.

**Examples**:

```julia
using FourierAnalysis, FFTW, LinearAlgebra, Statistics, Plots, DSP
t=128; lab=["x", "real(y)", "imag(y)"]

# Analytic signal of one vector
x=sinusoidal(10, 2, 128, t, π/2; DC=10) # cosine
y=analyticsignal(x)
# note that real(y) is x without the DC level, i.e., x=real(y)+DC
plot([x, real(y), imag(y)]; labels=lab)

# make a check
s=sinusoidal(10, 2, 128, t, 0) # sine
norm(s-imag(y)) # should be zero

# Analytic Signal by DSP.jl
y2=hilbert(x)
norm(s-imag(y2)) # should be zero
# DSP.jl does not remove the DC level
# thus x=real(y2) in this case
plot([x, real(y2), imag(y2)]; labels=lab)

# Analytic signal of multiple vectors
x=hcat(x, sinusoidal(10, 3, 128, t, π/2; DC=10))
y=analyticsignal(x)

# sliding-windows analytic signal of one vector
# (note edge effects)
x=sinusoidal(10, 2, 128, t*4, π/2; DC=0)
y=analyticsignal(x, t)
plot([x, real(y), imag(y)]; labels=lab)

# sliding-windows analytic signal of multiple vectors
x=hcat(x, sinusoidal(10, 3, 128, t*4, π/2; DC=0))
y=analyticsignal(x, t)
```
