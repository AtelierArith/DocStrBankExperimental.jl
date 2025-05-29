```julia
    Fill(value, kernel)
```

Construct an instance of [`Fill`](@ref) by designating a `value` and a `kernel` which will be used to infer an appropriate padding.

A minimal amount of padding is added which ensures that a convolution between the image and the kernel is defined at the boundary.

#### Usage illustration

Use `Fill(0,Kernel.sobel())` to specify a value of zero and the minimal amount of padding necessary to ensure that convolution with [`Kernel.sobel`](@ref) will be defined at the borders of an image.
