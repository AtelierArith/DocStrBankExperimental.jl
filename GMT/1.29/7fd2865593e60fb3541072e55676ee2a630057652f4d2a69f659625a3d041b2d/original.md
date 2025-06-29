```
J = imhmax(I::GMTimage{<:UInt8, 2}, H; conn=4)::GMTimage
```

Suppress regional maxima in image using H-maxima transform.

The H-maxima transform decreases the height of all regional maxima by an amount up to `H`. As a result, the transform fully suppresses regional maxima whose height is less than `H`. Regional maxima are connected pixels with the same intensity value, t, that are surrounded by pixels with an intensity value less than t.

### Args

  * `I::GMTimage{<:UInt8, 2}`: Input image.
  * `H`: Bump's maximum regional height.

### Kwargs

  * `conn::Int=4`: Connectivity value used to identify the regional maxima in I (4 or 8). Default is 4.

### Returns

A new $GMTimage$ of the same type as `I`.

### Example

```julia
a = fill(UInt8(10),10,10);
a[2:4,2:4] .= UInt8(13);
a[6:8,6:8] .= UInt8(18);
I = imhmax(mat2img(a), 4);
```
