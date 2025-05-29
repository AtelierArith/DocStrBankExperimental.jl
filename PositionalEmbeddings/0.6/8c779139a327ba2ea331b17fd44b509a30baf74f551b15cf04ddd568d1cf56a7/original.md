```
create_padding_mask(lengths::Vector{Int}, max_len::Int)
```

Create padding masks for batched sequences of varying lengths. This ensures that padded positions (positions beyond each sequence's actual length) are masked out and don't participate in attention.

# Arguments

  * `lengths::Vector{Int}`: Actual length of each sequence in the batch
  * `max_len::Int`: Maximum sequence length (padded length)

# Returns

  * 3D boolean array of shape (batch*size, max*len, 1) where True indicates padded positions

# Examples

```
# For 2 sequences of lengths 2 and 3, padded to length 4:
julia> mask = create_padding_mask([2, 3], 4)[:,:,1]
2×4 Matrix{Bool}:
 0  0  1  1  # First sequence: length 2, positions 3-4 are padding
 0  0  0  1  # Second sequence: length 3, position 4 is padding
```

# Usage with Causal Mask

Padding and causal masks are often combined for batched autoregressive tasks:

```
seq_len = 5
batch_lengths = [3, 4]

# Create both masks
causal = create_causal_mask(seq_len)                # Shape: (5, 5, 1)
padding = create_padding_mask(batch_lengths, seq_len) # Shape: (2, 5, 1)

# Combine masks which will either prevent attending to future tokens or padding tokens
combined = causal .| padding

# final_mask will prevent:
# 1. Attending to future tokens (from causal mask)
# 2. Attending to padding tokens (from padding mask)
```
