```
RoPE(head_size::Int, seq_len::Int;
    base::Number=10_000,
    scale::Number=1.0)
```

Rotary Position Embeddings (RoPE) implementation as described in the paper "RoFormer: Enhanced Transformer with Rotary Position Embedding".

Construct a RoPE object with the following arguments:

  * `head_size::Int`: Head size to apply rotation to (must be multiple of 2)
  * `seq_len::Int`: Maximum sequence length to support
  * `base::Number=10_000`: Base for geometric progression of frequencies
  * `scale::Number=1.0`: Scaling factor for the frequencies

# Examples

```julia
# Create RoPE for a model with 512 head size and max sequence length of 1024
rope = RoPE(512, 1024)

# Apply RoPE to input tensor of shape (head_size, seq_len, nheads*batch_size)
Q = randn(Float32, 512, 100, 32)
Q_positioned = rope(x)
```
