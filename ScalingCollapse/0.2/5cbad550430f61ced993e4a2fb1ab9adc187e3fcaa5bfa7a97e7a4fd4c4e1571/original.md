```
ScalingProblem(args...; kwargs...)
```

Create a scaling problem which solves on initialization.

# Arguments

  * `xs`: x values of the data
  * `ys`: y values of the data
  * `es`: y error values of the data (optional)
  * `Ls`: system sizes of the data

For more information on the arguments, see methods(ScalingCollapse.unzip_data).

# Keyword Arguments

  * `sf::ScalingFunction=ScalingFunction(preset; kwargs...)`: scaling function
  * `p_space::Vector{StepRangeLen}=[0.1:0.1:3.0 for _ in sf.p_names]`: parameter search space
  * `dx::Vector{Float64}=[-Inf, Inf]`: optimization interval
  * `quality::QualityFunction=Linear()`: quality function
  * `quality_scan::QualityFunction=MultipleSplines(scan_mode=true)`: quality function for the   parameter space scan (it is highly recommended to use the default function here)
  * `verbose::Bool=false`: print information during optimization
  * `starting_ps::Vector{Float64}`: If `starting_ps` are given, there will be no initial   parameter space scan. Instead, the optimization will start at the given points. This is   much faster, but might not find the global minimum.
  * `error::Bool=true`: If `error=true`, the error analysis will be performed to give   estimates of the uncertainties of the optimal parameters.

# Fields

  * `data::Vector{Data}`: data to be scaled
  * `sf::ScalingFunction`: scaling function
  * `p_space::Vector{StepRangeLen}`: search parameter space
  * `dx::Vector{Float64}`: optimization interval
  * `optimal_ps::Vector{Float64}`: optimal parameters
  * `optimal_ps_error::Vector{Float64}`: uncertainties of the optimal parameters
  * `minimum::Float64`: minimum of the objective function
  * `solved::Bool`: `true` if optimization was called
  * `verbose::Bool`: print information during optimization
  * `error::Bool`: perform error analysis
  * `quality_scan::QualityFunction`: quality function for the parameter space scan
  * `quality::QualityFunction`: quality function
  * `skip_scan::Bool`: `true` if `starting_ps` are given by the user
  * `starting_ps::Vector{Float64}`: starting points for the optimization
  * `errors_defined::Bool`: `true` if errors are given by the user

# Examples

```julia
using ScalingCollapse
```

### rescale the x axis only

```julia
# (e.g. for ys == binder cumulant of Ising model)
ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:x; p_names=["T_c", "nu"]),
    p_space=[0.1:0.1:3.0, 0.1:0.1:3.0],
    dx=[-1.0, 1.0],
)

# or the same but with errors
ScalingProblem(xs, ys, es, Ls;
    sc=ScalingFunction(:x; p_names=["T_c", "nu"]),
    p_space=[0.1:0.1:3.0, 0.1:0.1:3.0],
    dx=[-1.0, 1.0],
)
```

### rescale the x and y axis

```julia
# (e.g. for ys == magnetization of Ising model)
ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:xy; p_names=["T_c", "nu", "beta"]),
    dx=[-1.0, 1.0],
)
```

### rescale the x and y axis, but y axis with negative exponent

```julia
# (e.g. for ys == susceptibility of Ising model)
ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:xny; p_names=["T_c", "nu", "gamma"]),
    dx=[-1.0, 1.0],
)
```
