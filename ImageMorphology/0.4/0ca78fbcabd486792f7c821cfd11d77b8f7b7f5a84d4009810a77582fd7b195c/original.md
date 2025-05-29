```
opening!(out, img, buffer; [dims], [r])
opening!(out, img, se, buffer)
```

The in-place version of [`opening`](@ref) with input image `img` and output image `out`. The intermediate erosion result is stored in `buffer`.
