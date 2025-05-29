```
AbsolutePE{T<:AbstractArray}
AbsolutePE(embedding_size::Int, max_length::Int; base::Number=10_000)
```

Absolute Position Embeddings using sinusoidal frequencies from "Attention Is All You Need" paper. Formula: PE(pos,2i) = sin(pos/10000^(2i/d*model))         PE(pos,2i+1) = cos(pos/10000^(2i/d*model))

# Fields

  * `embedding_size::Int`: Size of the embedding dimension (d_model)
  * `max_length::Int`: Maximum sequence length supported
  * `embeddings::T`: Positional embeddings
