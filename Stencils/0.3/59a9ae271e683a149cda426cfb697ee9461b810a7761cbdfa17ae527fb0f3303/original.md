```
kernelproduct(hood::AbstractKernelStencil)
kernelproduct(hood::Stencil, kernel)
```

Returns the vector dot product of the stencil and the kernel, although differing from `dot` in that it is not taken iteratively for members of the stencil - they are treated as scalars.
