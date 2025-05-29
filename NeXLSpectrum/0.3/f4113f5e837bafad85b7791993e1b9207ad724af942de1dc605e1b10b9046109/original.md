```
annotate(
    img::AxisArray; 
    scale::Bool = true,
    coords::Union{Nothing, AbstractArray{<:AbstractDict{Symbol, <:AbstractFloat}}} = nothing,
    spectra::Union{Nothing, <:AbstractArray{<:Spectrum}} = nothing,
    thumbnails::Union{Nothing, AbstractArray{<:AxisArray}}=nothing,
    labelcoords::Bool = true,
    labelthumbnails::Bool = true,
    marker::Colorant = HSVA(60, 1, 1, 0.3) 
)
```

Add annotations like scale-bars, acquisition points, image areas to an image and display the result.

  * `coords` and `spectra` display as circles (with/without numeric labels).
  * `thumbnails` display as rectangles overlaying the image
  * `scale` displays as a scale-bar in the upper-right corner
  * `marker` is the color of the annotations which is by-default slightly transparent
