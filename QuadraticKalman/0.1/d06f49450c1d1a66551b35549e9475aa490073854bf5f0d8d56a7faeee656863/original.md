```
AugStateParams(N::Int, mu::AbstractVector{T}, Phi::AbstractMatrix{T}, 
               Sigma::AbstractMatrix{T}, B::AbstractMatrix{T}, 
               C::Vector{<:AbstractMatrix{T}}) where {T<:Real}
```

Construct an augmented state parameters object that encapsulates extended dynamics for the quadratic measurement model. This function computes additional structures  and matrices based on the traditional state-space parameters so that quadratic  components in the measurement equation are properly addressed during filtering  and smoothing.

# Arguments

  * N::Int: The dimension of the state vector.
  * mu::AbstractVector{T}: The initial state mean vector.
  * Phi::AbstractMatrix{T}: The state transition matrix.
  * Sigma::AbstractMatrix{T}: The covariance matrix for the state innovations.
  * B::AbstractMatrix{T}: The measurement design matrix.
  * C::Vector{<:AbstractMatrix{T}}: A vector of quadratic coefficient matrices for each  measurement element. Each element must be an N×N matrix representing the quadratic  contribution to the measurement equation.

# Returns

An instance of AugStateParams with the following fields:

  * mu_aug: Augmented state mean vector computed from mu and Sigma.
  * Phi_aug: Augmented state transition matrix derived from mu and Phi.
  * B_aug: Augmented measurement matrix computed from B and the set of matrices in C.
  * H_aug: Augmented selection matrix utilized in transforming state-space representations.
  * G_aug: Augmented duplication matrix used to handle symmetry in quadratic forms.
  * Lambda: A matrix computed to capture the structural features of the quadratic terms.
  * L1, L2, L3: Auxiliary matrices derived from Sigma and Lambda, supporting moment computations.
  * P: An integer indicating the total augmented state dimension, given by N + N^2.

# Details

The function performs the following steps:

1. Computes Lambda via a helper function, which encapsulates key aspects of the quadratic  measurement formulation.
2. Computes the augmented state mean (mu_aug) using the original mean and the covariance Sigma.
3. Computes the augmented state transition matrix (Phi_aug) by transforming Phi in accordance with  the augmented dynamics.
4. Determines the augmented measurement matrix (B_aug) by combining the original B with the quadratic  coefficient matrices C.
5. Calculates auxiliary matrices L1, L2, and L3 that are essential for subsequent moment and variance computations.
6. Generates selection and duplication matrices (H and G) using helper functions, and further refines them  to H*aug and G*aug to fit the augmented context.
7. Sets P, the overall augmented state dimension, to be the sum of the original state dimension and its square.

Ensure that all helper functions (e.g., compute*Lambda, compute*mu*aug, compute*Phi*aug, compute*B*aug,  compute*L1, compute*L2, compute*L3, selection*matrix, duplication*matrix, compute*H*aug, and compute*G*aug)  are defined and in scope prior to invoking this function.
