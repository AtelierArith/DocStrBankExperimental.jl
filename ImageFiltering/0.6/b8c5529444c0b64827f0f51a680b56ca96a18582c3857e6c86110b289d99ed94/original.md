```julia
    Pad(style, kernel)
    Pad(style)(kernel)
```

Construct an instance of [`Pad`](@ref) by designating the value `val` and a filter array `kernel` which will be used to determine the amount of padding from the `axes` of `kernel`.

#### Usage illustration

Use `Pad(:circular,Kernel.sobel())` to specify a `:circular` border style and the minimal amount of padding necessary to ensure that convolution with [`Kernel.sobel`](@ref) will be defined at the borders of an image.

---
