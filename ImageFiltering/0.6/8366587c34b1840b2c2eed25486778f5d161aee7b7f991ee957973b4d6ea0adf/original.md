```
imfilter!(imgfilt, img, kernel, [border="replicate"], [alg])
imfilter!(r, imgfilt, img, kernel, border::Pad)
imfilter!(r, imgfilt, img, kernel, border::NoPad, [inds=axes(imgfilt)])
```

Filter an array `img` with kernel `kernel` by computing their correlation, storing the result in `imgfilt`.

The indices of `imgfilt` determine the region over which the filtered image is computed–-you can use this fact to select just a specific region of interest, although be aware that the input `img` might still get padded.  Alteratively, explicitly provide the indices `inds` of `imgfilt` that you want to calculate, and use `NoPad` boundary conditions. In such cases, you are responsible for supplying appropriate padding: `img` must be indexable for all of the locations needed for calculating the output. This syntax is best-supported for FIR filtering; in particular, that that IIR filtering can lead to results that are inconsistent with respect to filtering the entire array.

See also: [`imfilter`](@ref).
