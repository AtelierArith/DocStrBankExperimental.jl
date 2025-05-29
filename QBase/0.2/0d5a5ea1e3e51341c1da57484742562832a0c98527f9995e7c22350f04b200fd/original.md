```
partial_trace(
    ρ :: AbstractMatrix, dims :: Vector{Int64}, id :: Int64
) :: Matrix
```

Performs the partial trace on matrix `ρ` with respect to the subsystem at the specified `id` and returns resulting reduced matrix. The returned matrix is square with dimension equal to the product of `dims` with the element corresponding to `id` removed.

*Inputs:*

  * `ρ` : The matrix on which the partial trace is performed. This matrix should be square       and have dimension equal to the product of the `dims`.
  * `dims` :  A vector containing positive integer elements which specify the       dimension of each subsystem. *E.g.* A 3-qubit system has `dims = [2,2,2]`,       a system containing a qubit and a qutrit has `dims = [2,3]`.
  * `id` : A positive integer indexing the `dims` vector to signify       the subsystem to be traced out.

The partial trace can be understood as a quantum operation $\mathcal{E}$ mapping the input Hilbert space to the output Hilbert space, $\mathcal{E} \; : \; \mathcal{H}_X \rightarrow \mathcal{H}_Y$. A quantum operation admits the operator sum representation, $\mathcal{E}(\rho) = \sum_i E_i  \rho E_i^{\dagger}$. For example, given a 3-qubit system with density matrix $\rho_{ABC}$, the partial trace with respect to system $B$, is explicitly,

$$
\rho_{AC} = \text{Tr}_B[\rho_{ABC}] = \mathcal{E}_B(\rho_{ABC}) = \sum_i E_i \rho_{ABC} E_i^{\dagger}
$$

where $E_i = \mathbb{I}_A \otimes \langle i |_B \otimes\mathbb{I}_C$, represents the Kraus operators for the quantum operation and $\rho_{AC}$ is the reduced density operator remaining after system $B$ is traced out.

A `DomainError` is thrown if `ρ` is not square or of proper dimension.
