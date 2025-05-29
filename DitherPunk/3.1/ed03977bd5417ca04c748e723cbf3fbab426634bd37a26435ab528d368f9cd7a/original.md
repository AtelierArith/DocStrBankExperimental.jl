```
dither([T::Type,] img, alg::AbstractDither, args...; kwargs...)
```

Dither image `img` using algorithm `alg`.

# Output

If no return type is specified, `dither` will default to the type of the input image.
