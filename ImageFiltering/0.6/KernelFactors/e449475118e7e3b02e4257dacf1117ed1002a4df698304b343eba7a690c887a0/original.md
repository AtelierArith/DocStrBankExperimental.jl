`KernelFactors` is a module implementing separable filtering kernels, each stored in terms of their factors. The following kernels are supported:

  * `sobel`
  * `prewitt`
  * `ando3`, `ando4`, and `ando5` (the latter in 2d only)
  * `scharr`
  * `bickley`
  * `gaussian`
  * `IIRGaussian` (approximate gaussian filtering, fast even for large σ)

See also: [`Kernel`](@ref).
