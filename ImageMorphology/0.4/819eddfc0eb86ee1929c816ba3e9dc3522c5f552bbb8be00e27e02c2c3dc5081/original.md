```
bothat!(out, img, buffer; [dims], [r])
bothat!(out, img, se, buffer)
```

The in-place version of [`bothat`](@ref) with input image `img` and output image `out`. The intermediate dilation result is stored in `buffer`.
