```
calculateToeplitzKernel!(f::Array{Complex{T}}, p::AbstractNFFTPlan, tr::Matrix{T}, fftplan)
```

Calculate the kernel for an implementation of the Gram matrix that utilizes its Toeplitz structure and writes it in-place in `f`, which has to be twice the size of the desired image matrix, as the Toeplitz trick requires an oversampling factor of 2 (cf. [Wajer, F. T. A. W., and K. P. Pruessmann. "Major speedup of reconstruction for sensitivity encoding with arbitrary trajectories." Proc. Intl. Soc. Mag. Res. Med. 2001.](https://cds.ismrm.org/ismrm-2001/PDF3/0767.pdf)). The type of the kernel `f` has to be `Complex{T}`, i.e. the complex of the k-space trajectory's type; for speed and memory efficiecy, call this function with `Float32.(tr)`, and set the type of `f` accordingly.

# Required Arguments

  * `f::Array{T}`: Array in which the kernel will be written.
  * `p::AbstractNFFTPlan`: NFFTPlan with the same dimensions as `tr`, which will be overwritten in place.
  * `tr::Matrix{T}`: non-Cartesian k-space trajectory in units revolutions/voxel, i.e. `tr[i] ∈ [-0.5, 0.5] ∀ i`. The matrix has the size `2 x Nsamples` for 2D imaging with a trajectory length `Nsamples`, and `3 x Nsamples` for 3D imaging.
  * `fftplan`: plan for the final FFT of the kernel from image to k-space. Therefore, it has to have twice the size of the original image. Calculate, e.g., with `fftplan = plan_fft(zeros(Complex{T}, 2 .* shape); flags=FFTW.MEASURE)`, where `shape` is the size of the reconstructed image.

# Examples

```jldoctest; output = false, setup = :(using NFFT, NFFTTools, Random; Random.seed!(1))
julia> using FFTW

julia> Nx = 32;

julia> trj = Float32.(rand(2, 1000) .- 0.5);

julia> p = plan_nfft(trj, (2Nx,2Nx))
NFFTPlan with 1000 sampling points for an input array of size(64, 64) and an output array of size(1000,) with dims 1:2

julia> fftplan = plan_fft(zeros(ComplexF32, (2Nx,2Nx)); flags=FFTW.MEASURE);

julia> λ = Array{ComplexF32}(undef, 2Nx, 2Nx);

julia> calculateToeplitzKernel!(λ, p, trj, fftplan);

julia> y = randn(ComplexF32, Nx, Nx);

julia> convolveToeplitzKernel!(y, λ);

```
