```
RotaryPositionalEmbedding(
    dim::IntegerType; max_sequence_length::IntegerType=4096, base::IntegerType=10000
)
```

Rotary Positional Embedding. For details see [su2024roformer](@citet).

The traditional implementation rotates consecutive pairs of elements in the feature dimension while the default implementation rotates pairs with stride half the feature dimensions for efficiency.

## Arguments

  * `dim`: The feature dimensions to be rotated. If the input feature is larger than dims then the rest is left unchanged.

## Keyword Arguments

  * `base`: The base used to compute angular frequency for each dimension in the positional encodings. Default: `10000`.
  * `max_sequence_length`: The maximum sequence length. Default: `4096`.

## Input

  * 4D AbstractArray s.t.

      * size(x, 1) == dim
      * size(x, 3) ≤ max*sequence*length

## Returns

  * 4D AbstractArray of the same size as the input.

## States

  * NamedTuple containing `cos_cache` and `sin_cache`.
