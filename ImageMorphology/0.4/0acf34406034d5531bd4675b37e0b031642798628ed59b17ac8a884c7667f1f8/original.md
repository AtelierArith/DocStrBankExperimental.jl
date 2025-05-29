```
tophat!(out, img, buffer; [dims], [r])
tophat!(out, img, se, buffer)
```

The in-place version of [`tophat`](@ref) with input image `img` and output image `out`. The intermediate erosion result is stored in `buffer`.
