```
G = img2grid(I::GMTimage; type=eltype(I.image))
```

Converts an GMTimage object to a grid. If the `type` option is not set the image data type is preserved and the array in NOT copied. Otherwise the image data is converted to the specified type and a copy is made.
