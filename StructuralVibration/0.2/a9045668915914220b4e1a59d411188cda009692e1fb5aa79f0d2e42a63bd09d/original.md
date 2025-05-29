```
HarmonicModalTimeProblem(K, M, ξn, u0, t, F, ω = 0., n = size(K, 1); ismodal = false)
```

Structure containing data for the modal time solver for computing the forced response due to an harmonic excitation

**Constructor**

  * `K::VecOrMat{Real}`:

      * If `ismodal = false` then `Matrix{Real}`: Stiffness matrix
      * If `ismodal = true` then `Vector{Real}`: Natural angular frequencies
  * `M::AbtractMatrix`:

      * If `ismodal = false`: Mass matrix
      * If `ismodal = true`: Mass-normalized mode shapes
  * `ξn`: Damping ratios
  * `u0::Tuple`: Initial conditions

      * `u0[1]`: Initial displacement (or modal displacement)
      * `u0[2]`: Initial velocity (or modal velocity)
  * `t::AbstractRange`: Time points at which to evaluate the response
  * `F::Real`: External force matrix (or modal participation factors)
  * `freq::Real`: Excitation frequency
  * `n::Int`: Number of modes to retain in the modal basis
  * `ismodal::Bool`: Flag to indicate if the problem contains modal data

**Fields**

  * `K`: Stiffness matrix (or modal stiffness matrix)
  * `M`: Mass matrix (or mass-normalized mode shapes)
  * `ξn`: Damping ratios
  * `u0`: Initial conditions

      * `u0[1]`: Initial displacement (or modal displacement)
      * `u0[2]`: Initial velocity (or modal velocity)
  * `t`: Time points at which to evaluate the response
  * `F`: Amplitude vector (or modal participation vector)
  * `ω`: Excitation angular frequency
  * `n`: Number of modes to retain in the modal basis
  * `ismodal`: Flag to indicate if the problem contains modal data
