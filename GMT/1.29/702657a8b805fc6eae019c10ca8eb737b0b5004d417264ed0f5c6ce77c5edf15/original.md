```
[I =] grays2cube(layers::GMTimage{UInt8,2}...; names::Vector{String}=String[], save::String="") -> GMTimage
```

Take N grayscale UInt8 GMTimages and agregate them into an image cube. Optionally provide a vector of names for each layer. If the `save` option is provided, we save the cube as a GeoTIFF file. Note, no need to provide an extension as the output name will always be '*.tiff'.

### Example

```juliadoc
# Make a cube with the Cb, Cr, a* and b* comonents of YCbCR & La*b* color spaces of an RGB image
I = mat2image(rand(UInt8,128, 128, 3))		# Create sample RGB image
_,Cb,Cr = rgb2YCbCr(I, Cb=true, Cr=true);	# Extract Cb and Cr components
L,a,b   = rgb2lab(I, L=true);				# Extract La*b* components
Icube = grays2cube(Cb, Cr, a, b; names=["Cb", "Cr", "a", "b"]);
```
