Draw an image.

This function can draw an image either from reading a file or using a two-dimensional array and the current colormap.

:param image: an image file name or two-dimensional array

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = LinRange(-2, 2, 40)
julia> y = LinRange(0, pi, 20)
julia> z = sin.(x') .+ cos.(y)
julia> # Draw an image from a 2d array
julia> imshow(z)
julia> # Draw an image from a file
julia> imshow("example.png")
```
