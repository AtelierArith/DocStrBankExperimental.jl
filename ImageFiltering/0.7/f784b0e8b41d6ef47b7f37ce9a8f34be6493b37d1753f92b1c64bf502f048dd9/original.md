```
imfilter!(r::AbstractResource, imgfilt, img, kernel::Tuple{TriggsSdika...}, border)
imfilter!(r::AbstractResource, imgfilt, img, kernel::TriggsSdika, dim::Integer, border)
```

Filter an array `img` with a Triggs-Sdika infinite impulse response (IIR) `kernel`, storing the result in `imgfilt`. Unlike the `FIR` and `FFT` algorithms, this version is safe for inplace operations, i.e., `imgfilt` can be the same array as `img`.

Either specify one kernel per dimension (as a tuple), or a particular dimension `dim` along which to filter. If you exhaust `kernel`s before you run out of array dimensions, the remaining dimension(s) will not be filtered.

With Triggs-Sdika filtering, the only border options are `NA()`, `"replicate"`, or `Fill(value)`.

See also: [`imfilter`](@ref), [`KernelFactors.TriggsSdika`](@ref), [`KernelFactors.IIRGaussian`](@ref).
