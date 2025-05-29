```
mgradient!(out, img, buffer; [dims], [r], [mode])
mgradient!(out, img, se, buffer; [mode])
```

The in-place version of [`mgradient`](@ref) with input image `img` and output image `out`.

The `buffer` array is required for `:beucher` mode. For `:internal` and `:external` modes, `buffer` is not needed and can be `nothing`.
