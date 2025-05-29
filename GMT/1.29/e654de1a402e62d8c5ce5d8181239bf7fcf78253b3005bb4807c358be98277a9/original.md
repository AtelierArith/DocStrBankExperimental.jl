```
I = grays2rgb(bandR, bandG, bandB, GI=nothing) -> GMTimage
```

Take three grayscale images as UInt8 matrices or GMTimages and compose an RGB image by simply copying the values of each band into the respective color channel of the output image. When the inputs are UInt8 matrices optionally provide a GMTgrid or GMTimage as fourth argument to set georeferencing info on output. The output is always a GMTimage object.

Note, do not confuse this function with `ind2rgb` that takes a single indexed image and creates a RGB using the image's colormap.

### Example

```juliadoc
I1 = mat2img(rand(UInt8, 16,16)); I2 = mat2img(rand(UInt8, 16,16)); I3 = mat2img(rand(UInt8, 16,16));
Irgb = grays2rgb(I1,I2,I3)
```
