```
DPModel{T<:AbstractFloat, M, CT, SB<:AbstractVector{T}, S<:AbstractVector{T}} <: AbstractNLPModel{T, S}
```

Dual perspective model for optimization problems, extending `AbstractNLPModel` with KL-regularized least squares functionality.

# Fields

  * `A::M`: Constraint matrix defining the linear system
  * `b::SB`: Target vector in the linear system Ax ≈ b
  * `c::S`: Cost vector for the objective function (defaults to ones)
  * `q::S`: Prior distribution vector for KL divergence term (defaults to uniform 1/n)
  * `λ::T`: Regularization parameter controlling the strength of the KL term (default: √eps)
  * `C::CT`: Positive definite scaling matrix for the linear system (default: Identity)
  * `mbuf::S`: First m-dimensional buffer for internal computations
  * `mbuf2::S`: Second m-dimensional buffer for internal computations
  * `nbuf::S`: n-dimensional buffer for internal computations
  * `bNrm::T`: Cached norm of vector b for scaling purposes
  * `scale::T`: Problem scaling factor (default: 1.0)
  * `lse::LogExpFunction`: Log-sum-exp function for computing KL divergence
  * `name::String`: Optional identifier for the problem instance
  * `meta::NLPModelMeta{T,S}`: Problem metadata required by NLPModels interface
  * `counters::Counters`: Performance counters for operation tracking

# Parameters

  * `T`: Floating point type for numerical computations
  * `M`: Matrix type for the constraint matrix, must be a subtype of AbstractMatrix
  * `CT`: Type of the scaling matrix
  * `SB`: Vector type for the right-hand side, must be a subtype of AbstractVector{T}
  * `S`: Vector type for solution and workspace vectors, must be a subtype of AbstractVector{T}

# Examples

```julia
# Create a simple dual perspective model
A = randn(10, 5)
b = randn(10)
model = DPModel(A=A, b=b)

# Create model with custom regularization
model = DPModel(A=A, b=b, λ=1e-3)

# Simplified model creation:
model = DPModel(A, b)
```
