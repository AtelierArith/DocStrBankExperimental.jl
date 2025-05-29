```julia
mutable struct TransientSolution{T, N, A, B} <: VoronoiFVM.AbstractTransientSolution{T, N, A, B}
```

Transient solution structure

## Fields

  * `u::Any`: Vector of solutions

  * `t::Any`: Vector of times

## Interface

Object of this type adhere to the `AbstractDiffEqArray`  interface. For indexing and interpolation, see [https://diffeq.sciml.ai/stable/basics/solution/](https://diffeq.sciml.ai/stable/basics/solution/).

In particular, a TransientSolution `sol` can be accessed as follows:

  * `sol[i]` contains the solution for timestep `i`
  * `sol[ispec,:,i]` contains the solution for component `ispec` at timestep `i`
  * `sol(t)` returns a (linearly) interpolated solution value for `t`.
  * `sol.t[i]` is the corresponding time for timestep `i`
  * `sol[ispec,ix,i]` refers to solution of component `ispec` at node `ix` at moment `i`
