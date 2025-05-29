```
AugStateParams{T<:Real, T2<:Real}
```

An augmented state parameter container designed for quadratic measurement models. This type extends the conventional state-space representation to incorporate quadratic measurement features, enabling advanced filtering and smoothing algorithms to effectively handle non-linear measurement equations.

Fields:

  * mu_aug::AbstractVector{T}:   The augmented state mean vector, which integrates the original state mean with additional terms arising from quadratic components.
  * Phi_aug::AbstractMatrix{T}:   The augmented state transition matrix. It extends the traditional state transition dynamics to include quadratic interactions.
  * B_aug::AbstractMatrix{T}:   The augmented measurement matrix that relates the extended state vector to the observed measurements, accounting for both linear and quadratic effects.
  * H_aug::AbstractMatrix{T}:   The augmented selection matrix used in mapping the original state space to the augmented space, facilitating the extraction of relevant subcomponents.
  * G_aug::AbstractMatrix{T}:   The augmented duplication matrix, which assists in preserving the symmetry properties of quadratic forms when processing covariance or moment adjustments.
  * Lambda::AbstractMatrix{T2}:   A core structural matrix that captures the key quadratic interactions within the model. Its specific formulation supports the reconstruction of quadratic measures.
  * L1::AbstractMatrix{T}:   An auxiliary matrix used for computing first-order moment corrections in the augmented state representation.
  * L2::AbstractMatrix{T}:   An auxiliary matrix involved in the computation of second-order moment adjustments, contributing to the accurate determination of state covariances.
  * L3::AbstractMatrix{T}:   An auxiliary matrix designed to support higher-order moment computations, often necessary for fine-tuning the filtering process.
  * P::Int:   The total augmented state dimension, typically defined as the sum of the original state dimension and the square of the state dimension.

This structure is pivotal for models that incorporate quadratic measurement equations, allowing for the direct integration of quadratic terms into the state estimation process. It facilitates the derivation of augmented transition and measurement matrices, which are essential for achieving improved filtering and smoothing performance in non-linear state-space models.
