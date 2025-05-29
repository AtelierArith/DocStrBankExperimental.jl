```
convolveToeplitzKernel!(y::Array{T,N}, λ::Array{T,N}[, fftplan = plan_fft(λ; flags=FFTW.ESTIMATE), ifftplan = plan_ifft(λ; flags=FFTW.ESTIMATE), xOS1 = similar(λ), xOS2 = similar(λ)])
```

Convolves the image `y` with the Toeplitz kernel `λ` and overwrites `y` with the result. `y` is also returned for convenience. As this function is commonly applied many times, it is highly recommended to pre-allocate / pre-compute all optional arguments. By doing so, this entire function is non-allocating.

# Required Arguments

  * `y::Array{T,N}`: Input image that will be overwritten with the result. `y` is a matrix (`N=2`) for 2D imaging and a 3D tensor (`N=3`) for 3D imaging. The type of the elements `T` must match the ones of `λ`.
  * `λ::Array{T,N}`: Toeplitz kernel, which as to be the same type as `k`, but twice the size due to the required oversampling (cf. [`calculateToeplitzKernel`](@ref)).

# Optional, but highly recommended Arguments

  * `fftplan`: plan for the oversampled FFT, i.e. it has to have twice the size of the original image. Calculate, e.g., with `fftplan = plan_fft(λ; flags=FFTW.MEASURE)`, where `shape` is the size of the reconstructed image.
  * `ifftplan`: plan for the oversampled inverse FFT. Calculate, e.g., with `ifftplan = plan_ifft(λ; flags=FFTW.MEASURE)`, where `shape` is the size of the reconstructed image.
  * `xOS1`: pre-allocated array of the size of `λ`. Pre-allocate with `xOS1 = similar(λ)`.
  * `xOS2`: pre-allocated array of the size of `λ`. Pre-allocate with `xOS2 = similar(λ)`.

# Examples

```jldoctest; output = false, setup = :(using NFFT, NFFTTools, Random; Random.seed!(1))
julia> using FFTW

julia> Nx = 32;

julia> trj = Float32.(rand(2, 1000) .- 0.5);

julia> λ = calculateToeplitzKernel((Nx, Nx), trj);

julia> xOS1 = similar(λ);

julia> xOS2 = similar(λ);

julia> fftplan = plan_fft(xOS1; flags=FFTW.MEASURE);

julia> ifftplan = plan_ifft(xOS1; flags=FFTW.MEASURE);

julia> y = randn(ComplexF32, Nx, Nx);

julia> convolveToeplitzKernel!(y, λ, fftplan, ifftplan, xOS1, xOS2)
32×32 Matrix{ComplexF32}:
  177.717-52.0493im   10.6059+20.7185im  …   746.131+330.005im
 -311.858+988.219im  -1216.83-1295.14im      410.732+751.925im
 -1082.27+872.968im   1023.97-1556.45im     -923.699+478.63im
 -999.035-525.161im  -1694.59-658.558im     -521.044+607.005im
 -342.999+1481.82im  -1729.18-2712.81im      56.5212+1394.81im
 -1187.65-1979.55im   1389.67+970.033im  …   2968.93-744.264im
 -666.533+485.511im  -1315.83+409.855im     -610.146+132.258im
  1159.57+64.6059im  -299.169-569.622im      663.802+396.827im
 -795.112-1464.63im   -462.43+2442.77im     -1622.72+1701.27im
 -1047.67+31.5578im  -1127.65-936.043im      474.071+797.911im
         ⋮                               ⋱
  327.345+2191.71im  -904.635+558.786im     -1449.32-276.721im
  -1047.2-71.362im    363.109+567.346im      -1974.0-2348.36im
 -1540.45+1661.77im   1175.75+1279.75im  …   1110.61+653.234im
 -526.832-435.297im  -265.021-2019.08im      68.5607-323.086im
 -1076.52-2719.16im  -477.005+2232.06im      -155.59-1275.66im
  1143.76-735.966im  -380.489+2485.78im      1812.17-261.191im
  1685.44-1243.29im   1911.16-1157.72im     -991.639-42.8214im
  1054.11-1282.41im   66.9358-588.991im  …  -952.238+1026.35im
 -417.276-273.367im  -946.698+1971.77im     -890.339-882.05im

```
