Replace NaNs in an array with a specified value.

```
Usage: (newimg, mask) = replacenan(img, defaultval=0)

Arguments:
   img        - The Array containing NaN values.
   defaultval - The default value to replace NaNs.

Returns:
        newim - Filled image,
        mask  - Boolean image indicating non-NaN regions in the original
                image.
```

See also: [`fillnan`](@ref)
