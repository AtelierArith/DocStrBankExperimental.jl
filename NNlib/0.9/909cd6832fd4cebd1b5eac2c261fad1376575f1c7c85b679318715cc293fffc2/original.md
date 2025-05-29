```
dot_product_attention(query, key, value, [bias]; [fdrop, mask, nheads])
```

Multihead dot product attention used in transformer architectures.

The input arrays must have the first two dimensions given by the number of features and the sequence length, then an arbitrary number of batch dimensions or none.

Returns the attention output array of size `(v_dim, q_len, batch_size...)` and the attention scores of size `(kv_len, q_len, nheads, batch_size...)`.

See also [`dot_product_attention_scores`](@ref) if you only need the attention scores.

# Arguments

  * `query`: Query array of size `(qk_dim, q_len, batch_size...)`.
  * `key`: Key array of size `(qk_dim, kv_len, batch_size...)`.
  * `value`: Value array of size `(v_dim, kv_len, batch_size...)`.
  * `bias`: Either `nothing` or an array broadcastable to size `(kv_len, q_len, nheads, batch_size)`.         It will be added to the attention scores before applying the softmax. Default `nothing`.
  * `fdrop`: A dropout function or layer to be applied on the attention scores right after the softmax.          Default `identity` (no dropout).
  * `mask`: Either `nothing` or a boolean array broadcastable to size `(kv_len, q_len, nheads, batch_size)`.         The mask is applied to the attention scores just before the softmax.         See [`make_causal_mask`](@ref) fore creating causal masks. Default `nothing`.
  * `nheads`: Number of heads to split the input arrays into. Default `1`.

# Examples

```julia
q, k, v = rand(10, 20, 2), rand(10, 30, 2), rand(20, 30, 2)
y, α = dot_product_attention(q, k, v)
```
