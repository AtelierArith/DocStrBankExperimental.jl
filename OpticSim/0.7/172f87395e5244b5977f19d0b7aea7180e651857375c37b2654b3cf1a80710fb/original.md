```
triangulate(surf::ParametricSurface{S,N}, quads_per_row::Int, extensionu::Bool = false, extensionv::Bool = false, radialu::Bool = false, radialv::Bool = false)
```

Create an array of triangles representing the parametric surface where vertices are sampled on an even grid in UV space. The surface can be extended by 1% in u and v separately, and specifying either u or v as being radial - i.e. determining the radius on the surface e.g. rho for zernike - will result in that dimension being sampled using sqwrt so that area of triangles is uniform. The extension will also only apply to the maximum in this case.
