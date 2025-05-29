```
QKModel(N::Int, M::Int, mu::AbstractVector, Phi::AbstractMatrix,
        Omega::AbstractMatrix, A::AbstractVector, B::AbstractMatrix,
        C::Vector{<:AbstractMatrix}, D::AbstractMatrix,
        alpha::AbstractMatrix; check_stability::Bool=false) where {T<:Real}

QKModel(state::StateParams, meas::MeasParams; check_stability::Bool=false)
```

Creates a Quadratic Kalman Filter model specification.

# Arguments

  * `N::Int`: Dimension of the state vector
  * `M::Int`: Dimension of the measurement vector
  * `mu::AbstractVector`: Initial state mean vector (N×1)
  * `Phi::AbstractMatrix`: State transition matrix (N×N)
  * `Omega::AbstractMatrix`: State noise covariance matrix (N×N)
  * `A::AbstractVector`: Constant term in measurement equation (M×1)
  * `B::AbstractMatrix`: Linear measurement matrix (M×N)
  * `C::Vector{<:AbstractMatrix}`: Quadratic measurement matrices (Vector of M N×N matrices)
  * `D::AbstractMatrix`: Measurement noise covariance matrix (M×M)
  * `alpha::AbstractMatrix`: Measurement error higher moment parameter (M×M)

# Keyword Arguments

  * `check_stability::Bool=false`: If true, checks if the state transition dynamics are stable

# Alternative Constructor

The second method allows construction from pre-built StateParams and MeasParams objects.

# Returns

Returns a QKModel object containing all parameters needed for the quadratic Kalman filter.

# Examples

```julia
# Direct construction
N, M = 2, 1
model = QKModel(
    N, M,
    [0.0, 0.0],        # mu
    [0.9 0.0; 0.0 0.9], # Phi
    [0.1 0.0; 0.0 0.1], # Omega
    [0.0],              # A
    [1.0 1.0],          # B
    [reshape([1.0 0.0; 0.0 1.0], 2, 2)], # C
    [0.1],              # D
    [0.0]               # alpha
)

# Construction from components
state = StateParams(...)
meas = MeasParams(...)
model = QKModel(state, meas)
```

# Notes

  * All matrices must be properly sized according to N and M
  * The model components are used to construct augmented state representations
  * The stability check verifies that eigenvalues of Phi are within the unit circle
