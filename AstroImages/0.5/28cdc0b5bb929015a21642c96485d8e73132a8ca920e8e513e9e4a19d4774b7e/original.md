```
imview(img::AbstractArray{<:Complex}; ...)
```

When applied to an image with complex values, display the magnitude of the pixels using `imview` and display the phase angle as a panel below using a cyclical color map. For more customatization, you can create a view like this yourself:

```julia
vcat(
    imview(abs.(img)),
    imview(angle.(img)),
)
```
