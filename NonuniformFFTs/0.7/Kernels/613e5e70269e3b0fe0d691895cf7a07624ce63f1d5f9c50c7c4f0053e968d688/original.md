```
FastApproximation <: Kernels.EvaluationMode
```

Use a fast approximation or algorithm to efficiently evaluate a kernel.

The evaluation type depends on the actual kernel:

  * for [`KaiserBesselKernel`](@ref) and [`BackwardsKaiserBesselKernel`](@ref), this uses a fast piecewise polynomial approximation heavily inspired from FINUFFT;
  * for [`GaussianKernel`](@ref), this uses the fast Gaussian gridding algorithm proposed by Greengard & Lee (SIAM Rev. 2004);
  * for [`BSplineKernel`](@ref), this is currently the same as [`Direct`](@ref) evaluation.

In the first two cases, this is generally faster than [`Direct`](@ref) evaluation for CPU transforms.

On GPUs this is not necessarily the case, and results may depend on the actual GPU used. For example, on an Nvidia A100, `Direct` evaluation of the `KaiserBesselKernel` (which involves Bessel functions) seems to beat polynomial approximation, and is also a bit faster than the `BackwardsKaiserBesselKernel` (involving `sinh` functions).
