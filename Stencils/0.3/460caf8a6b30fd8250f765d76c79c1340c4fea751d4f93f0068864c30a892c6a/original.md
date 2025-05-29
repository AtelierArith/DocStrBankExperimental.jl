```
kernelproduct(hood::AbstractKernelStencil)
kernelproduct(hood::Stencil, kernel)
```

Take the vector dot produce of the stencil and the kernel, without recursion into the values of either. Essentially `Base.dot` without recursive calls on the contents, as these are rarely what is intended.
