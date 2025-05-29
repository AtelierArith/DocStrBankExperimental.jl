```
Kernel <: AbstractKernelStencil

Kernel(stencil::Stencil, kernel::AbstractArray)
Kernel(f::Function, stencil::Stencil)
```

Wrap any other stencil object, and includes a kernel array of the same length and positions as the stencil. A function of the stencil and kernel, like [`kernelproduct`](@ref) can be used in  [`mapstencil`](@ref).

A function `f` may be passed as the first argument, and a kernel array will be calculated with `map(f, distances(stencil))`.

As an example, Kernels can be convolved with an Array

```julia
using Stencils

# Define a random array that the kernel will be convolved with
r = rand(1000, 1000)

# Define kernel array
sharpen = [0 -1 0;
           -1 5 -1;
           0 -1 0]

# Define a stencil that is the same size as the kernel array
stencil = Window(1)

# Create a stencil Kernel from the stencil and the kernel array
k = Kernel(stencil, sharpen)

# Wrap the random array and the Kernel in a StencilArray
A = StencilArray(r, k)

# use `mapstencil` with the `kernelproduct` function to convolve the Kernel with array. 
# Note: `kernelproduce is similar to `Base.dot` but `kernelproduct` 
# lets you use an array of StaticArray and it will still work (dot is recursive).
mapstencil(kernelproduct, A) 
```
