```
ForcedModalTimeProblem(K, M, ξn, u0, t, F, n = size(K, 1); ismodal = false)
```

Structure containing data for modal time solver for computing the forced response due to an arbitrary excitation

**Fields**

  * `K::VecOrMat{Real}`:

      * If `ismodal = false` then `Matrix{Real}`: Stiffness matrix
      * If `ismodal = true` then `Vector{Real}`: Natural angular frequencies
  * `M::AbtractMatrix`:

      * If `ismodal = false`: Mass matrix
      * If `ismodal = true`: Mass-normalized mode shapes
  * `ξn`: Damping ratios
  * `F::Matrix{Real}`: External force matrix (or modal participation factors)
  * `u0::Tuple`: Initial conditions

      * `u0[1]`: Initial displacement (or modal displacement)
      * `u0[2]`: Initial velocity (or modal velocity)
  * `t::AbstractRange`: Time points at which to evaluate the response
  * `n::Int`: Number of modes to retain in the modal basis
  * `ismodal::Bool`: Flag to indicate if the problem contains modal data
