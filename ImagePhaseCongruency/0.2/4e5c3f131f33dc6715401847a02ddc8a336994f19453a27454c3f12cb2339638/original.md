Fill NaN values in an image with closest non NaN value.

This can be used as a crude (but quick) 'inpainting' function to allow a FFT to be computed on an image containing NaN values.  While the 'inpainting' is crude it is typically good enough to remove most of the edge effects one might get at the boundaries of the NaN regions.  The NaN regions should then be remasked out of the final processed image.

```
Usage:  (newim, mask) = fillnan(img)

  Argument:  img   - Image to be 'filled'.
  Returns:   newim - Filled image.
             mask  - Binary image indicating the valid, non-NaN, regions in
                     the original image.
```

See also: [`replacenan`](@ref)
