```
I2 = imfill(I; conn=4, is_transposed=true, layout="TRBa")
```

Fill holes in the grayscale $GMTimage$ I or UInt8 matrix I.

Here, a hole is defined as an area of dark pixels surrounded by lighter pixels.

### Args

  * `I::Union{GMTimage{UInt8, 2}, GMTimage{Bool, 2}, Matrix{UInt8}, Matrix{Bool}, BitMatrix}`: Input image.

### Kwargs

  * `conn::Int`: Connectivity for the image filling (4 or 8). Default is 4.
  * `is_transposed::Bool`: If `true`, it informs that the input image array is transposed. Default is `true`.  Normally the $GMTimage$ carries information to know about the transposition (which is `true` when the layout is "TRB").  When passing a matrix in column-major order (the default in Julia), `is_transposed` must be set to `false`.  NOTE: The deaful is `true` because that is the normal case when reading a file image with $gmtread$ or $gdalread$.
  * `layout::String`: Layout of the input Matrix (default is "TRBa"). If the input is a GMTimage,  this argument should have been set automatically and can normally be ignored.

### Returns

  * A new $GMTimage$ (or Matrix) with the holes filled.

### Examples

```julia
# Example from Matlab imfill
I = gmtread("TESTSDIR * "assets/coins.png");
Ibw = binarize(I);
BW2 = imfill(Ibw);
```
