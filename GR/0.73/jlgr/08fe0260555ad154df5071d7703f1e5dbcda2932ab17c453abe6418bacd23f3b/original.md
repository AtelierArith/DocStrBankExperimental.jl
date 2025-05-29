Draw an isosurface.

This function can draw an image either from reading a file or using a two-dimensional array and the current colormap. Values greater than the isovalue will be seen as outside the isosurface, while values less than the isovalue will be seen as inside the isosurface.

:param v: the volume data :param isovalue: the isovalue

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> s = LinRange(-1, 1, 40)
julia> v = 1 .- (s .^ 2 .+ (s .^ 2)' .+ reshape(s,1,1,:) .^ 2) .^ 0.5
julia> # Draw an image from a 2d array
julia> isosurface(v, isovalue=0.2)
```
