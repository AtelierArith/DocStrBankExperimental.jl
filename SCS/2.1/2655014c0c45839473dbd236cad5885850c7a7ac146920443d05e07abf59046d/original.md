```
scs_solve(linear_solver, args...)
```

The low-level interface to the SCS solver.

!!! warning
    This function is an advanced feature with a risk of incorrect usage. If you are a new user, we recommend that you use the JuMP or Convex interfaces instead.


## Problem definition

SCS solves a problem of the form

```
minimize        1/2 * x' * P * x + c' * x
subject to      A * x + s = b
                s in K
```

where K is a product cone of

  * zero cone
  * positive orthant `{ x | x ≥ 0 }`
  * box cone `{ (t,x) | t*l ≤ x ≤ t*u }`
  * second-order cone (SOC) `{ (t,x) | ||x||_2 ≤ t }`
  * semi-definite cone (SDC) `{ X | X is psd }`
  * exponential cone `{ (x,y,z) | y e^(x/y) ≤ z, y > 0 }`
  * power cone `{ (x,y,z) | x^a * y^(1-a) ≥ |z|, x ≥ 0, y ≥ 0 }`
  * dual power cone `{ (u,v,w) | (u/a)^a * (v/(1-a))^(1-a) ≥ |w|, u ≥ 0, v ≥ 0 }`

## Input arguments

The problem data are:

  * `linear_solver`: a `LinearSolver` to use
  * `m`: the number of affine constraints
  * `n`: the number of variables
  * `A`: an `AbstractMatrix` with `m` rows and `n` cols
  * `P`: the upper-triangular component of a positive semidefinite symmetric      matrix of size `(n, n)`
  * `b`: a `Vector` of length `m`
  * `c`: a `Vector` of length `n`

The rows of `A` correspond to cones in `K` and need to be specified in the order above by the following arguments.

  * `z`: the number of primal zero / dual free cones, i.e. primal equality constraints
  * `l`: the number of linear cones
  * `bu`: the `Vector` of upper bounds for the box cone
  * `bl`: the `Vector` of lower bounds for the box cone
  * `q`: the `Vector` of SOCs sizes
  * `s`: the `Vector` of SDCs sizes
  * `ep`: the number of primal exponential cones
  * `ed`: the number of dual exponential cones
  * `p`: the `Vector` of power cone parameters (±1, with negative values for the dual cone)

Provide a warm start to SCS by overriding:

  * `primal_sol = zeros(n)`: a `Vector` to warmstart the primal variables,
  * `dual_sol = zeros(m)`: a `Vector` to warmstart the dual variables,
  * `slack = zeros(m)`: a `Vector` to warmstart the slack variables.

!!! note
    To successfully warmstart the solver `primal_sol`, `dual_sol` and `slack` must all be provided **and** `warm_start` option must be set to `true`.


Finally, a number of kwarg arguments may be passed as options to the solver. The valid keywords are `fieldnames(ScsSettings)`. See the official SCS documentation for information on each keyword.

## Output

This function eturns a `Solution` object, which contains the following fields:

```julia
mutable struct Solution{T}
    x::Vector{Float64}
    y::Vector{Float64}
    s::Vector{Float64}
    info::ScsInfo{T}
    ret_val::T
end
```

where `x` stores the optimal value of the primal variable, `y` stores the optimal value of the dual variable, `s` is the slack variable, and `info` contains various information about the solve step.

!!! warning
    SCS expects the semi-definite cones to be scaled by a factor of √2. That is, the off-diagonal elements in the A matrix and b vector should be multiplied by √2, and then the corresponding rows in the dual and slack solution vectors should be multiplied by 1/√2.


`SCS.raw_status(::ScsInfo)::String` describes the status, e.g. `"solved"`, `"infeasible"`, `"unbounded"`, etc. For the precise return status, the value of `ret_val` field should be compared with https://github.com/cvxgrp/scs/blob/3aaa93c7aa04c7001df5e51b81f21b126dfa99b3/include/glbopts.h#L18.
