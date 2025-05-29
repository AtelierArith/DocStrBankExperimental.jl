```
kernelproduct(rule::NeighborhoodRule})
kernelproduct(hood::AbstractKernelNeighborhood)
kernelproduct(hood::Neighborhood, kernel)
```

Returns the vector dot product of the neighborhood and the kernel, although differing from `dot` in that the dot product is not take for vector members of the neighborhood - they are treated as scalars.
