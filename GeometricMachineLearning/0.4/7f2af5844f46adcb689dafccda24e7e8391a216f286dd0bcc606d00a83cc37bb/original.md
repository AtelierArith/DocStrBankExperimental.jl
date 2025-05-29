```
VolumePreservingAttention(dim, seq_length)
```

Make an instance of `VolumePreservingAttention` for a specific dimension and sequence length.

The sequence length is `0` by default. 

Setting `seq_length` to `0` for all sequence lengths but does not apply the fast Cayley activation.

# Arguments

The constructor can be called with an optional keyword argument: 

  * `skew_sym::Bool = false`: specifies if the weight matrix is skew symmetric (`true`) or arbitrary (`false`).

# Functor

Applying a layer of type `VolumePreservingAttention` does the following: 

  * First we perform the operation $Z \mapsto Z^T A Z =: C$, where $Z\in\mathbb{R}^{N\times\mathtt{seq\_length}}$ is a vector containing time series data and $A$ is the skew symmetric matrix associated with the layer (if `skew_sym = true`).
  * In a second step we compute the Cayley transform of $C$; $\Lambda = \mathrm{Cayley}(C)$.
  * The output of the layer is then $Z\Lambda$.

# Implementation

The fast activation is only implemented for sequence lengths of 2, 3, 4 and 5.  Other sequence lengths only work on CPU (for now).

The fast Cayley activation is using inverses that have been computed symbolically.
