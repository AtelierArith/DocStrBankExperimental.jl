```
    Contour <: AbstractComponentAnalysisAlgorithm
    Contour()
    analyze_components(components, f::Contour)
    analyze_components!(df::AbstractDataFrame, components, f::Contour)
```

Takes as input an array of labelled connected components and returns a `DataFrame` with columns that store the contours for each connected component.

If you require the information about the topology (hierarchy) of the contours you can use the `establish_contour_hierarchy` function to obtain a tree data structure that reflects the nesting of the contours and stores all the contour pixels in a [`DigitalContour`](@ref) type.

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ImageCore, AbstractTrees

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, Contour())

```

# Reference

1. S. Suzuki and K. Abe, “Topological structural analysis of digitized binary images by border following,” Computer Vision, Graphics, and Image Processing, vol. 29, no. 3, p. 396, Mar. 1985.
