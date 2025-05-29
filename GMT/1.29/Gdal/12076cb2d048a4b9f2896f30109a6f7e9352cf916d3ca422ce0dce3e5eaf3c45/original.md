```
Ic = bwareaopen(Ibw::Union{GMTimage{UInt8,2}, GMTimage{Bool,2}}; keepwhites::Bool=false, keepblacks::Bool=false, kwargs...)::GMTimage
```

Remove all connected components (groups of pixels) that have fewer than P pixels from the binary image $Ibw$.

Remove groups of pixels in the image that are smaller than a provided threshold size (in pixels) and replaces them with the pixel value of the largest neighbor polygon. This operation is known as an area opening. 

*Polygons* are determined as regions of the image where the pixels all have the same value, and that are contiguous (connected). The work is done by the GDAL $GDALSieveFilter$ function.

### Args

  * `I`: Input binary image. It can be a GMTimage object or a file name that once read by $gmtread$ returns a binary image.

### Kwargs

  * `keepwhites`: If set to `true` keeps all the white pixels (or true) in input image as white in the output image.  That is, only let the black pixels be set to white (or true).
  * `keepblacks`: If set to `true` keeps the black pixels (or false) in the input image as black in the output image.  That is, only let the white pixels be set to black (or false).
  * `threshold`: groups of pixels with sizes smaller than this will be merged into their largest neighbor.  The default is 10.
  * `conn`: Connectivity. Either 4 indicating that diagonal pixels are not considered directly adjacent for polygon  membership purposes or 8 indicating they are. The default is 4.
