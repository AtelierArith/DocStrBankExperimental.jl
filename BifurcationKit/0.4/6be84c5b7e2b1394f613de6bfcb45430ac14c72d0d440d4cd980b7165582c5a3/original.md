```julia
struct Flow{TF, Tf, Tts, Tff, Td, Tad, Tse, Tprob, TprobMono, Tfs, Tcb, Tδ} <: BifurcationKit.AbstractFlow
```

  * `F::Any`: The vector field `(x, p) -> F(x, p)` associated to a Cauchy problem. Used for the differential of the shooting problem. Default: nothing
  * `flow::Any`: The flow (or semigroup) `(x, p, t) -> flow(x, p, t)` associated to the Cauchy problem. Only the last time point must be returned in the form (u = ...) Default: nothing
  * `flowTimeSol::Any`: Flow which returns the tuple (t, u(t)). Optional, mainly used for plotting on the user side. Default: nothing
  * `flowFull::Any`: [Optional] The flow (or semigroup) associated to the Cauchy problem `(x, p, t) -> flow(x, p, t)`. The whole solution on the time interval [0,t] must be returned. It is not strictly necessary to provide this, it is mainly used for plotting on the user side. Please use `nothing` as default. Default: nothing
  * `jvp::Any`: The differential `dflow` of the flow *w.r.t.* `x`, `(x, p, dx, t) -> dflow(x, p, dx, t)`. One important thing is that we require `dflow(x, dx, t)` to return a Named Tuple: `(t = t, u = flow(x, p, t), du = dflow(x, p, dx, t))`, the last component being the value of the derivative of the flow. Default: nothing
  * `vjp::Any`: The adjoint differential `vjpflow` of the flow *w.r.t.* `x`, `(x, p, dx, t) -> vjpflow(x, p, dx, t)`. One important thing is that we require `vjpflow(x, p, dx, t)` to return a Named Tuple: `(t = t, u = flow(x, p, t), du = vjpflow(x, p, dx, t))`, the last component being the value of the derivative of the flow. Default: nothing
  * `jvpSerial::Any`: [Optional] Serial version of dflow. Used internally when using parallel multiple shooting. Please use `nothing` as default. Default: nothing
  * `prob::Any`: [Internal] store the ODEProblem associated to the flow of the Cauchy problem Default: nothing
  * `probMono::Any`: [Internal] store the ODEProblem associated to the flow of the variational problem Default: nothing
  * `flowSerial::Any`: [Internal] Serial version of the flow Default: nothing
  * `callback::Any`: [Internal] Store possible callback Default: nothing
  * `delta::Any`: [Internal] Default: 1.0e-8

# Simplified constructor(s)

We provide a simple constructor where you only pass the vector field `F`, the flow `ϕ` and its differential `dϕ`:

```
fl = Flow(F, ϕ, dϕ)
```

# Simplified constructors for DifferentialEquations.jl

These are some simple constructors for which you only have to pass a `prob::ODEProblem` or `prob::EnsembleProblem` (for parallel computation) from `DifferentialEquations.jl` and an ODE time stepper like `Tsit5()`. Hence, you can do for example

```
fl = Flow(prob, Tsit5(); kwargs...)
```

where `kwargs` is passed to `SciMLBase::solve`. If your vector field depends on parameters `p`, you can define a `Flow` using

```
fl = Flow(prob, Tsit5(); kwargs...)
```

Finally, you can pass two `ODEProblem` where the second one is used to compute the variational equation:

```
fl = Flow(prob1::ODEProblem, alg1, prob2::ODEProblem, alg2; kwargs...)
```
