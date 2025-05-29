```
RectangularBinEncoding <: Encoding
RectangularBinEncoding(binning::RectangularBinning, x)
RectangularBinEncoding(binning::FixedRectangularBinning)
```

An encoding scheme that [`encode`](@ref)s points `χ ∈ x` into their histogram bins.

The first call signature simply initializes a [`FixedRectangularBinning`](@ref) and then calls the second call signature.

See [`FixedRectangularBinning`](@ref) for info on mapping points to bins.
