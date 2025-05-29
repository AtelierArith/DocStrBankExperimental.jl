```
closing!(out, img, buffer; [dims], [r])
closing!(out, img, se, buffer)
```

The in-place version of [`closing`](@ref) with input image `img` and output image `out`. The intermediate dilation result is stored in `buffer`.
