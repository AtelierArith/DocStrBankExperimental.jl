```
MultiHeadAttention(dims; nheads=1, dense_kwargs=(; use_bias=False()),
                   attention_dropout_probability=0.0f0)
```

The multi-head dot-product attention layer used in Transformer architectures [vaswani2017attention](@citep).

## Arguments

  * `dims`: The embedding dimensions of inputs, intermediate tensors and outputs.         In the most general case, it is given as         a) `(q_in_dim, k_in_dim, v_in_dim) => (qk_dim, v_dim) => out_dim`.         Can take also simpler forms as         b) `dims::Int`;         c) `in_dim::Int => (qk_dim, v_dim) => out_dim`;         d) `in_dim::Int => qkv_dim => out_dim`.

## Keyword Arguments

  * `nheads`: number of heads.
  * `attention_dropout_probability`: dropout probability for the attention scores.
  * `dense_kwargs`: keyword arguments for the Dense layers. Default `use_bias=false`.

## Forward Pass Signature(s)

```
(m::MultiHeadAttention)(qkv, ps, st::NamedTuple)
(m::MultiHeadAttention)((q, kv), ps, st::NamedTuple)
(m::MultiHeadAttention)((q, k, v, [mask = nothing]), ps, st::NamedTuple)
```

## Inputs

  * `qkv`: a single input tensor for query, key and value. This corresponds to self-attention.
  * `(q, kv)`: a tuple of two input tensors for query and key-value.
  * `(q, k, v)`: a tuple of three input tensors for query, key and value.
  * `mask`: an optional mask to apply to the attention scores. This must be broadcastable to the shape of the attention scores `(kv_len, q_len, nheads, batch_size)`.

The query tensor `q` is expected to have shape `(q_in_dim, q_len, batch_size)`, the key test `k` is expected to have shape `(k_in_dim, kv_len, batch_size)`, the value tensor `v` is expected to have shape `(v_in_dim, kv_len, batch_size)`.

## Returns

  * A tuple of two elements. The first element is the output tensor of shape `(out_dim, q_len, batch_size)` and the second element is the attention scores of shape `(q_len, kv_len, nheads, batch_size)`.
  * A NamedTuple of the states of the layer.

# Extended Help

## Examples

```jldoctest
julia> m = MultiHeadAttention(64; nheads=8);

julia> ps, st = Lux.setup(Random.default_rng(), m);

julia> q = randn(Float32, 64, 10, 32);

julia> k = randn(Float32, 64, 20, 32);

julia> v = randn(Float32, 64, 20, 32);

julia> (y, α), st_new = m((q, k, v), ps, st);

julia> size(y)
(64, 10, 32)

julia> size(α)
(20, 10, 8, 32)

julia> (y, α), st_new = m(q, ps, st);  # self-attention

julia> size(y)
(64, 10, 32)

julia> size(α)
(10, 10, 8, 32)
```
