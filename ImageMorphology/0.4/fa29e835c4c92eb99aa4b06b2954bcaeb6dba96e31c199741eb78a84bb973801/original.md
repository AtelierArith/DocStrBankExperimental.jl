```
mlaplacian!(out, img, buffer; [dims], [r])
mlaplacian!(out, img, se, buffer)
```

The in-place version of [`mlaplacian`](@ref) with input image `img` and output image `out`. The intermediate erosion result is stored in `buffer`.
