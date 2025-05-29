```julia
random_matrix_product_state(
    ::Type{T},
    n::Int64,
    chi::Int64
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}
random_matrix_product_state(
    ::Type{T},
    n::Int64,
    chi::Int64,
    d::Int64
) -> TensorInference.TensorNetworkModel{OMEinsum.DynamicNestedEinsum{Int64}}

```

Matrix product state (MPS) is a tensor network model that is widely used in quantum many-body physics. It is a special case of tensor network model where the tensors are rank-3 tensors and the physical indices are connected in a chain. The MPS is defined as:

$$
\begin{align*}
\left| \psi \right\rangle &= \sum_{x_1, x_2, \ldots, x_n} \text{Tr}(A_1^{x_1} A_2^{x_2} \cdots A_n^{x_n}) \left| x_1, x_2, \ldots, x_n \right\rangle \\
\left\langle \psi \right| &= \sum_{x_1, x_2, \ldots, x_n} \text{Tr}(A_n^{x_n} \cdots A_2^{x_2} A_1^{x_1}) \left\langle x_1, x_2, \ldots, x_n \right|
\end{align*}
$$

where $A_i^{x_i}$ is a rank-3 tensor with physical index $x_i$ and two virtual indices connecting to the next tensor. The MPS is a special case of the tensor network model where the tensors are rank-3 tensors and the physical indices are connected in a chain.

### Arguments

  * `n` is the number of physical indices.
  * `chi` is the bond dimension of the virtual indices.
  * `d` is the dimension of the physical indices.
