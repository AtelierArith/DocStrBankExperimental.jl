```
imfilter!(::AbstractResource, imgfilt, img, kernel, NoPad(), [inds=axes(imgfilt)])
```

Filter an array `img` with kernel `kernel` by computing their correlation, storing the result in `imgfilt`, defaulting to a finite-impulse response (FIR) algorithm. Any necessary padding must have already been supplied to `img`. If you want padding applied, instead call

```
imfilter!([r::AbstractResource,] imgfilt, img, kernel, border)
```

with a specific `border`, or use

```
imfilter!(imgfilt, img, kernel, [Algorithm.FIR()])
```

for default padding.

If `inds` is supplied, only the elements of `imgfilt` with indices in the domain of `inds` will be calculated. This can be particularly useful for "cascaded FIR filters" where you pad over a larger area and then calculate the result over just the necessary/well-defined region at each successive stage.

See also: [`imfilter`](@ref).
