```
Encoding
```

The supertype for all encoding schemes. Encodings always encode elements of input data into the positive integers. The encoding API is defined by the functions [`encode`](@ref) and [`decode`](@ref). Some probability estimators utilize encodings internally.

Current available encodings are:

  * [`OrdinalPatternEncoding`](@ref).
  * [`GaussianCDFEncoding`](@ref).
  * [`RectangularBinEncoding`](@ref).
  * [`RelativeMeanEncoding`](@ref).
  * [`RelativeFirstDifferenceEncoding`](@ref).
  * [`UniqueElementsEncoding`](@ref).
  * [`BubbleSortSwapsEncoding`](@ref).
  * [`PairDistanceEncoding`](@ref).
  * [`CombinationEncoding`](@ref), which can combine any of the above encodings.
