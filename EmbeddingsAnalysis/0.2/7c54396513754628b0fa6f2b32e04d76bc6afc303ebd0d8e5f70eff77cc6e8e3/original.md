```
compress(wv [;kwargs...])
```

Compresses `wv::WordVectors` by using array quantization.

# Keyword arguments

  * `sampling_ratio::AbstractFloat` specifies the percentage of vectors to use

for quantization codebook creation

  * `k::Int` number of quantization values for a codebook
  * `m::Int` number of codebooks to use
  * `method::Symbol` specifies the array quantization method
  * `distance::PreMetric` is the distance

Other keyword arguments specific to the quantization methods can also be provided.
