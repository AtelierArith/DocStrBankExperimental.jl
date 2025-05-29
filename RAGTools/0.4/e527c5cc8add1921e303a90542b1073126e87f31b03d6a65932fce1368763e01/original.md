```
find_closest(
	finder::BitPackedCosineSimilarity, emb::AbstractMatrix{<:Bool},
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, rescore_multiplier::Int = 4, minimum_similarity::AbstractFloat = -1.0, kwargs...)
```

Finds the indices of chunks (represented by embeddings in `emb`) that are closest to query embedding (`query_emb`) using bit-packed binary embeddings (in the index).

This is a two-pass approach:

  * First pass: Hamming distance in bit-packed binary form to get the `top_k * rescore_multiplier` (i.e., more than top_k) candidates.
  * Second pass: Rescore the candidates with float embeddings and return the top_k.

Returns only `top_k` closest indices.

Reference: [HuggingFace: Embedding Quantization](https://huggingface.co/blog/embedding-quantization#binary-quantization-in-vector-databases).

# Examples

Convert any Float embeddings to bit-packed binary like this:

```julia
bitpacked_emb = pack_bits(emb.>0)
```
