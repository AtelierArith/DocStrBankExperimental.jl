```julia
mutable struct DiscreteLinearSystem{T1<:(AbstractMatrix{<:Real}), T2<:(AbstractMatrix{<:Real}), T3<:(AbstractMatrix{<:Real}), T4<:(AbstractMatrix{<:Real}), IP<:(Union{var"#s2873", var"#s2872"} where {var"#s2873"<:Causal.Inport, var"#s2872"<:Nothing}), OP<:(Union{var"#s2871", var"#s2870"} where {var"#s2871"<:Causal.Outport, var"#s2870"<:Nothing}), ST<:(AbstractVector{<:Real}), RH, RO, var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDiscreteSystem
```

Constructs a `DiscreteLinearSystem` with `input` and `output`. `state` is the initial state and `t` is the time. `modelargs` and `modelkwargs` are passed into `ODEProblem` and `solverargs` and `solverkwargs` are passed into `solve` method of `DifferentialEquations`. `alg` is the algorithm to solve the differential equation of the system.

The `DiscreteLinearSystem` is represented by the following state and output equations.

$$
\begin{array}{l}
    \dot{x} = A x + B u \\[0.25cm]
    y = C x + D u 
\end{array}
$$

where $x$ is `state`. `solver` is used to solve the above differential equation.

# Fields

  * `A::AbstractMatrix{<:Real}`: A
  * `B::AbstractMatrix{<:Real}`: B
  * `C::AbstractMatrix{<:Real}`: C
  * `D::AbstractMatrix{<:Real}`: D
  * `input::Union{var"#s2873", var"#s2872"} where {var"#s2873"<:Causal.Inport, var"#s2872"<:Nothing}`: Input. Expected to an `Inport` or `Nothing`
  * `output::Union{var"#s2871", var"#s2870"} where {var"#s2871"<:Causal.Outport, var"#s2870"<:Nothing}`: Output port
  * `state::AbstractVector{<:Real}`: State
  * `righthandside::Any`: Right-hand-side function
  * `readout::Any`: Readout function
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `t::Any`
  * `modelargs::Any`
  * `modelkwargs::Any`
  * `solverargs::Any`
  * `solverkwargs::Any`
  * `alg::Any`
  * `integrator::Any`
