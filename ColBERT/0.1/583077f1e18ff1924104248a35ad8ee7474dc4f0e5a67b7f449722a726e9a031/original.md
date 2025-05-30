```
index(index_path::String, bert::HF.HGFBertModel, linear::Layers.Dense,
    tokenizer::TextEncoders.AbstractTransformerTextEncoder,
    collection::Vector{String}, dim::Int, index_bsize::Int,
    doc_token::String, skiplist::Vector{Int}, num_chunks::Int,
    chunksize::Int, centroids::AbstractMatrix{Float32},
    bucket_cutoffs::AbstractVector{Float32}, nbits::Int)
```

Build the index using for the `collection`.

The documents are processed in batches of size `chunksize` (see [`setup`](@ref)). Embeddings and document lengths are computed for each batch (see [`encode_passages`](@ref)), and they are saved to disk along with relevant metadata (see [`save_chunk`](@ref)).

# Arguments

  * `index_path`: Path where the index is to be saved.
  * `bert`: The pre-trained BERT component of the ColBERT model.
  * `linear`: The pre-trained linear component of the ColBERT model.
  * `tokenizer`: Tokenizer to be used.
  * `collection`: The collection to index.
  * `dim`: The embedding dimension.
  * `index_bsize`: The batch size used for running the transformer.
  * `doc_token`: The document token.
  * `skiplist`: List of tokens to skip.
  * `num_chunks`: Total number of chunks.
  * `chunksize`: The maximum size of a chunk.
  * `centroids`: Centroids used to compute the compressed representations.
  * `bucket_cutoffs`: Cutoffs used to compute the residuals.
  * `nbits`: Number of bits to encode the residuals in.
