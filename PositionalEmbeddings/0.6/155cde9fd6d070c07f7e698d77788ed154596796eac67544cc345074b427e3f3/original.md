```
(rope::RoPE)(x) -> AbstractArray
```

Apply Rotary Position Embeddings to the input array `x` of shape `(head_size, seq_len, batch * num_heads)`.

# Arguments

  * `x`: Input array where first dimension must match `rope.head_size` and second dimension must not exceed      the maximum cached sequence length.

See also: [`RoPE`](@ref)
