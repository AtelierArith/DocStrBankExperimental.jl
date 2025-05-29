```julia
mutable struct LorenzSystem{T1<:Real, T2<:Real, T3<:Real, T4<:Real, RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}), OP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

Constructs a `LorenzSystem` with `input` and `output`. `sigma`, `beta`, `rho` and `gamma` is the system parameters. `state` is the initial state and `t` is the time. `modelargs` and `modelkwargs` are passed into `ODEProblem` and `solverargs` and `solverkwargs` are passed into `solve` method of `DifferentialEquations`. `alg` is the algorithm to solve the differential equation of the system.

If `input` is `nothing`, the state equation of `LorenzSystem` is 

$$
\begin{array}{l}
    \dot{x}_1 = \gamma (\sigma (x_2 - x_1)) \\[0.25cm]
    \dot{x}_2 = \gamma (x_1 (\rho - x_3) - x_2) \\[0.25cm]
    \dot{x}_3 = \gamma (x_1 x_2 - \beta x_3) 
\end{array}
$$

where $x$ is `state`. `solver` is used to solve the above differential equation. If `input` is not `nothing`, then the state eqaution is

$$
\begin{array}{l}
    \dot{x}_1 = \gamma (\sigma (x_2 - x_1)) + \sum_{j = 1}^3 \alpha_{1j} u_j \\[0.25cm]
    \dot{x}_2 = \gamma (x_1 (\rho - x_3) - x_2) + \sum_{j = 1}^3 \alpha_{2j} u_j \\[0.25cm]
    \dot{x}_3 = \gamma (x_1 x_2 - \beta x_3) + \sum_{j = 1}^3 \alpha_{3j} u_j 
\end{array}
$$

where $A = [lpha_{ij}]$ is `cplmat` and $u = [u_{j}]$ is the value of the `input`. The output function is 

$$
    y = g(x, u, t)
$$

where $t$ is time `t`, $y$ is the value of the `output` and $g$ is `outputfunc`.

# Fields

  * `σ::Real`: α
  * `β::Real`: β
  * `ρ::Real`: ρ
  * `γ::Real`: γ
  * `righthandside::Any`: Right-hand-side function
  * `readout::Any`: Readout function
  * `state::AbstractVector{<:Real}`: State
  * `input::Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}`: Input. Expected to be an `Inport` or `Nothing`
  * `output::Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}`: Output port
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
