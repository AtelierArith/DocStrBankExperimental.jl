```
DirectTimeProblem(K, M, C, F, u0, t)
```

Structure containing data for the time solver

**Constructor**

  * `K::AbstractMatrix`: Stiffness matrix
  * `M::AbstractMatrix`: Mass matrix
  * `C:AbstractMatrix`: Damping matrix
  * `F::AbstractMatrix`: External force matrix
  * `u0::Tuple`: Initial conditions

      * `u0[1]`: Initial displacement (or modal displacement)
      * `u0[2]`: Initial velocity (or modal velocity)
  * `t::AbstractVector`: Time points at which to evaluate the response

**Fields**

  * `K`: Stiffness matrix
  * `M`: Mass matrix
  * `C`: Damping matrix
  * `F`: External force matrix
  * `u0`: Initial conditions

      * `u0[1]`: Initial displacement
      * `u0[2]`: Initial velocity
  * `h::Real`: Time step
