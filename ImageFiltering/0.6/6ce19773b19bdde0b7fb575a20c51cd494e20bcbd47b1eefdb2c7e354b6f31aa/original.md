```
imfilter!(::AbstractResource{FFT}, imgfilt, img, kernel, NoPad())
```

Filter an array `img` with kernel `kernel` by computing their correlation, storing the result in `imgfilt`, using a fast Fourier transform (FFT) algorithm. Any necessary padding must have already been applied to `img`. If you want padding applied, instead call

```
imfilter!(::AbstractResource{FFT}, imgfilt, img, kernel, border)
```

with a specific `border`, or use

```
imfilter!(imgfilt, img, kernel, Algorithm.FFT())
```

for default padding.

See also: [`imfilter`](@ref).
