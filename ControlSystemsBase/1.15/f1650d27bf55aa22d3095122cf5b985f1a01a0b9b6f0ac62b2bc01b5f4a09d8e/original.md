```
cont = observer_controller(sys, L::AbstractMatrix, K::AbstractMatrix; direct=false)
```

# If `direct = false`

Return the observer_controller `cont` that is given by `ss(A - B*L - K*C + K*D*L, K, L, 0)` such that `feedback(sys, cont)` produces a closed-loop system with eigenvalues given by `A-KC` and `A-BL`.

This controller does not have a direct term, and corresponds to state feedback operating on state estimated by [`observer_predictor`](@ref). Use this form if the computed control signal is applied at the next sampling instant, or with an otherwise large delay in relation to the measurement fed into the controller.

Ref: "Computer-Controlled Systems" Eq 4.37

# If `direct = true`

Return the observer controller `cont` that is given by `ss((I-KC)(A-BL), (I-KC)(A-BL)K, L, LK)` such that `feedback(sys, cont)` produces a closed-loop system with eigenvalues given by `A-BL` and `A-BL-KC`. This controller has a direct term, and corresponds to state feedback operating on state estimated by [`observer_filter`](@ref). Use this form if the computed control signal is applied immediately after receiveing a measurement. This version typically has better performance than the one without a direct term.

!!! note
    To use this formulation, the observer gain `K` should have been designed for the pair `(A, CA)` rather than `(A, C)`. To do this, pass `direct = true` when calling [`place`](@ref) or [`kalman`](@ref).


Ref: Ref: "Computer-Controlled Systems" pp 140 and "Computer-Controlled Systems" pp 162 prob 4.7

# Arguments:

  * `sys`: Model of system
  * `L`: State-feedback gain `u = -Lx`
  * `K`: Observer gain

See also [`observer_predictor`](@ref) and [`innovation_form`](@ref).
