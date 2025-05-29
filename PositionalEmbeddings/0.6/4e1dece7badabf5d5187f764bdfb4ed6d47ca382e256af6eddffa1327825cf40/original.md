```
create_causal_mask(seq_len::Int)
```

Create a causal (autoregressive) attention mask that prevents positions from attending to future positions. This is commonly used in language models to ensure predictions only depend on previous tokens.

The mask ensures that position i can only attend to positions j ≤ i, creating a triangular pattern where the upper triangle including diagonal is masked (True) and the lower triangle is unmasked (False).

# Arguments

  * `seq_len::Int`: Length of the sequence to create mask for

# Returns

  * 3D boolean array of shape (seq*len, seq*len, 1) where True indicates positions to mask

# Examples

```
julia> mask = create_causal_mask(3)[:,:,1]
3×3 Matrix{Bool}:
 1  1  1  # First position can't attend anything
 0  1  1  # Second position can attend to first only
 0  0  1  # Third position can attend to first and second
```
