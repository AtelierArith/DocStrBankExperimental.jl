```
LanczosKernel([T=Float64,] S, B=Flat)
```

yields an instance of a Lanczos re-sampling kernel of support size `S` (which must be even), for floating-point type `T` and boundary conditions `B`.

The Lanczos re-sampling kernels are even cardinal functions which tend to be normalized for large support size.  They are defined by (see also https://en.wikipedia.org/wiki/Lanczos_resampling):

```
ker(x) = S/(2*(π*x)^2)*sin(π*x)*sin(2*π*x/S)     if |x| ≤ S/2
         0                                       if |x| ≥ S/2
```

The expression `ker'` yields the first derivative of a Lanczos re-sampling kernel `ker` (also see the constructor [`LanczosKernelPrime`](@ref)).
