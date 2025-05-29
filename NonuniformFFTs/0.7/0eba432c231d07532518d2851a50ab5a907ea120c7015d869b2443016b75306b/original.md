```
PlanNUFFT([T = ComplexF64], dims::Dims; ntransforms = Val(1), backend = CPU(), kwargs...)
```

Construct a plan for performing non-uniform FFTs (NUFFTs).

The created plan contains all data needed to perform NUFFTs for non-uniform data of type `T` (`ComplexF64` by default) and uniform data with dimensions `dims`.

# Extended help

## Optional keyword arguments

  * `ntransforms = Val(1)`: the number of simultaneous transforms to perform. This is useful if one wants to transform multiple scalar quantities at the same non-uniform points.
  * `backend::KernelAbstractions.Backend = CPU()`: corresponds to the device type where everything will be executed. This could be e.g. `CUDABackend()` if CUDA.jl is loaded.

### NUFFT parameters

The following parameters control transform accuracy. The default values give a relative accuracy of the order of $10^{-7}$ for `Float64` or `ComplexF64` data.

  * `m = HalfSupport(4)`: the half-support of the convolution kernels. Large values increase accuracy at the cost of performance.
  * `σ = 2.0`: NUFFT oversampling factor. Typical values are 2.0 (more accurate) and 1.25 (faster), but other values such as 1.5 should also work.
  * `kernel::AbstractKernel = BackwardsKaiserBesselKernel()`: convolution kernel used for NUFFTs.

### Main performance parameters

  * `kernel_evalmode`: method used for kernel evaluation. The default is [`FastApproximation`](@ref) on CPU, which will attempt to use a fast approximation method which greatly speeds up kernel evaluation. On GPUs the default is [`Direct`](@ref), as the fast approximation method is not necessarily faster.
  * `block_size`: the block size (in number of elements) when using block partitioning or when sorting is enabled. This enables spatial sorting of points, even when `sort_points = False()` (which actually permutes point data for possibly faster memory accesses). The block size can be tuned for maximal performance. It can either be passed as an `Int` (linear block size) or as a tuple `(B₁, …, Bₙ)` to specify the block size in each Cartesian direction. The current default is 4096 on the CPU and around 1024 on the GPU (but depends on the number of dimensions). These may change in the future or even depend on the actual computing device. On the CPU, using block partitioning is required for running with multiple threads. On the GPU, this option is ignored if `gpu_method = :shared_memory`. Blocking / spatial sorting can be completely disabled by passing `block_size = nothing` (but this is generally slower).
  * `gpu_method`: allows to select between different implementations of GPU transforms. Possible options are:

      * `:global_memory` (default): directly read and write onto arrays in global memory in spreading (type-1) and interpolation (type-2) operations;
      * `:shared_memory`: copy data between global memory and shared memory (local to each GPU workgroup) and perform most operations in the latter, which is faster and can help avoid some atomic operations in type-1 transforms. We try to use as much shared memory as is typically available on current GPUs (which is typically 48 KiB on CUDA and 64 KiB on AMDGPU). Note that this method completely ignores the `block_size` parameter, as the actual block size is adjusted to maximise shared memory usage. When this method is enabled, one can play with the `gpu_batch_size` parameter (see below) to further tune performance.

    For highly dense problems (number of non-uniform points comparable to the total grid size), the `:shared_memory` method can be much faster, especially when the `HalfSupport` is 4 or less (accuracies up to `1e-7` for `σ = 2`).
  * `fftw_flags = FFTW.MEASURE`: parameters passed to the FFTW planner when `backend = CPU()`.

### Other performance parameters

These are more advanced performance parameters which may disappear or whose behaviour may change in the future.

  * `sort_points = False()`: whether to internally permute the order of the non-uniform points. This can be enabled by passing `sort_points = True()`. This will generally require extra allocations since the input points need to be copied onto a new container. If this is enabled, more time will be spent in [`set_points!`](@ref) and less time on the actual transforms. This can improve performance if executing multiple transforms on the same non-uniform points. Note that, even when enabled, this does not modify the `points` argument passed to `set_points!`. This option is ignored when `block_size = nothing` (which disables spatial sorting).
  * `gpu_batch_size = Val(Np)`: minimum batch size used in type-1 transforms when `gpu_method = :shared_memory`. The idea is that, to avoid inefficient atomic operations on shared-memory arrays, we process non-uniform points in batches of `Np` points. The actual value of `Np` will typically be larger than the input one in order to maximise shared memory usage within each GPU workgroup. Note that larger `Np` also means that less shared memory space is available for local blocks, meaning that the effective block size can get smaller (which is not necessarily bad for performance, and can actually be beneficial). When tuning performance, it is helpful to print the plan (as in `println(plan)`) to see the actual block and batch sizes.

### Other parameters

  * `fftshift = false`: determines the order of wavenumbers in uniform space. If `false` (default), the same order used by FFTW is used, with positive wavenumbers first (`[0, 1, 2, …, N÷2-1]` for even-size transforms) and negative ones afterwards (`[-N÷2, …, -1]`). Otherwise, wavenumbers are expected to be in increasing order (`[-N÷2, -kmax, …, -1, 0, 1, …, N÷2-1]`), which is compatible with the output in NFFT.jl and corresponds to applying the `AbstractFFTs.fftshift` function to the data. This option also corresponds to the `modeord` parameter in FINUFFT. This only affects complex-to-complex transforms.
  * `timer = TimerOutput()`: allows to specify a `TimerOutput` (from the [TimerOutputs.jl](https://github.com/KristofferC/TimerOutputs.jl) package) where timing information will be written to. By default the plan creates its own timer. One can visualise the time spent on different parts of the NUFFT computation using `p.timer`.
  * `synchronise = false`: if `true`, add synchronisation barrier between calls to GPU kernels. Enabling this is needed for accurate timings in `p.timer` when computing on a GPU, but may result in reduced performance.

## FFT size and performance

For performance reasons, when doing FFTs one usually wants the size of the input along each dimension to be a power of 2 (ideally), or the product of powers of small prime numbers (2, 3, 5, …). The problem is that, with the NUFFT, one does not directly control the FFT size due to the oversampling factor $σ$, which may be any real number $σ > 1$. That is, for an input of size $N$, FFTs are performed on an oversampled grid of size $Ñ ≈ σN$. Note that $σN$ is generally not an integer, hence the $≈$.

The aim of this section is to clarify how $Ñ$ is actually chosen, so that one can predict its value for given inputs $N$ and $σ$. This may be better understood in actual code:

```julia
Ñ = nextprod((2, 3, 5), floor(Int, σ * N))
```

Basically, we truncate $σN$ to an integer, and then we choose $Ñ$ as the next integer that can be written as the product of powers of 2, 3 and 5 (see [`nextprod`](https://docs.julialang.org/en/v1/base/math/#Base.nextprod)). Most often, the result will be greater than or equal to $σN$.

## Using real non-uniform data

In some applications, the non-uniform data to be transformed is purely real. In this case, one may pass `Float64` or `Float32` as the first argument. This may be faster than converting data to complex types, in particular because the real-to-complex FFTs from FFTW will be used to compute the transforms. Note that, in this case, the dimensions of the uniform data arrays is not exactly `dims`, since the size of the first dimension is divided roughly by 2 (taking advantage of Hermitian symmetry). For convenience, one can call [`size(::PlanNUFFT)`](@ref) on the constructed plan to know in advance the dimensions of the uniform data arrays.
