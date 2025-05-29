```
IVFADCIndex{U<:Unsigned, I<:Unsigned, Dc<:Distances.PreMetric, Dr<:Distances.PreMetric, T<:AbstractFloat, Q<:AbstractCoarseQuantizer{Dc,T}}
```

The inverse file system object. It allows for approximate nearest neighbor search into the contained vectors.

# Fields

  * `coarse_quantizer::AbstractCoarseQuantizer{Dc,T}` contains the coarse vectors
  * `residual_quantizer::QuantizedArrays.OrthogonalQuantizer{U,Dr,T,2}`

is employed to quantize vectors when adding to the index

  * `inverse_index::InvertedIndex{I,U}` is the actual inverse index employed

to perform the search.
