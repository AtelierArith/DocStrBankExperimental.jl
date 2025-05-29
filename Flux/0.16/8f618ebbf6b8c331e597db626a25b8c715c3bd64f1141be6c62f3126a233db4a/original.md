```
MultiHeadAttention(dims; [nheads, bias, init, dropout_prob])
```

The multi-head dot-product attention layer used in Transformer architectures [1].

Returns the transformed input sequence and the attention scores.

[1] Vaswani et al. "Attention is all you need." Advances in Neural Information Processing Systems. 2017.

# Arguments

  * `dims`: The embedding dimensions of inputs, intermediate tensors and outputs.         In the most general case, it is given as          a) `(q_in_dim, k_in_dim, v_in_dim) => (qk_dim, v_dim) => out_dim`.         Can take also simpler forms as         b) `dims::Int`;         c) `in_dim::Int => (qk_dim, v_dim) => out_dim`;         d) `in_dim::Int => qkv_dim => out_dim`.
  * `nheads`: number of heads. Default `8`.
  * `init`: weight initializer for the Dense layers. Default `glorot_uniform`.
  * `bias` : whether pointwise QKVO dense transforms use bias. Default `false`.
  * `dropout_prob`: dropout probability for the attention scores. Default `0.0`.

# Forward

```
(mha::MultiHeadAttention)(q_in, k_in, v_in, [bias]; [mask])
```

The arguments of the forward pass are:

  * `q_in`: Input query array of size `(q_in_dim, q_len, batch_size)`.
  * `k_in`: Input key array of size `(k_in_dim, kv_len, batch_size)`.
  * `v_in`: Input value array of size `(v_in_dim, kv_len, batch_size)`.
  * `bias`: Bias array broadcastable to size `(kv_len, q_len, nheads, batch_size)`.          It will be added to the attention scores before the softmax.         Default `nothing`.
  * `mask`: Input array broadcastable to size          `(kv_len, q_len, nheads, batch_size)`.          The mask is applied to the attention scores just before the softmax.          See [`NNlib.make_causal_mask`](@ref) for creating causal masks.          Default `nothing`.

Alternative calling signatures are `mha(q_in)`, equivalent to `mha(q_in, q_in, q_in)` (self-attention), and `mha(q_in, k_in)`, equivalent to `mha(q_in, k_in, k_in)` (key and value are the same).

See also [`NNlib.dot_product_attention`](@ref).

# Examples

```julia
mha = MultiHeadAttention(64, nheads = 8)
q = rand(Float32, (64, 10, 32))
k = rand(Float32, (64, 20, 32))
v = rand(Float32, (64, 20, 32))
y, α = mha(q, k, v) 
# [y] = [64, 10, 32]
# [α] = [20, 10, 8, 32]

mha = MultiHeadAttention(64 => 1024 => 1024, nheads = 8)
y, α = mha(q) # self-attention
# [y] = [1024, 10, 32]
# [α] = [10, 10, 8, 32]
```
