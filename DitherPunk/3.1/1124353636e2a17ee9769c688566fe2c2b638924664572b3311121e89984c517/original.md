```
dither!([out,] img, alg::AbstractDither, args...; kwargs...)
```

Dither image `img` using algorithm `alg`.

# Output

If `out` is specified, it will be changed in place. Otherwise `img` will be changed in place.
