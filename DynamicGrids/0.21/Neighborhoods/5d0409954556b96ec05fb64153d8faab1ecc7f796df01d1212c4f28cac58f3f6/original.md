```
kernelproduct(hood::AbstractKernelNeighborhood)
kernelproduct(hood::Neighborhood, kernel)
```

Take the vector dot produce of the neighborhood and the kernel, without recursion into the values of either. Essentially `Base.dot` without recursive calls on the contents, as these are rarely what is intended.
