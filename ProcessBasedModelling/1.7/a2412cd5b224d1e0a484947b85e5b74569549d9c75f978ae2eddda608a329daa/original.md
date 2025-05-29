```
processes_to_mtkmodel(processes::Vector [, default]; kw...)
```

Construct a ModelingToolkit.jl model/system using the provided `processes` and `default` processes. The model/system is *not* structurally simplified. Use the function [`processes_to_mtkeqs`](@ref) to obtain the raw `Vector{Equation}` before it is passed to the MTK model/system like `ODESystem`.

During construction, the following automations improve user experience:

  * Variable(s) introduced in `processes` that does not themselves have a process obtain a default process from `default`.
  * If no default exists, but the variable(s) have a default numerical value, a [`ParameterProcess`](@ref) is created for said variable(s) and a warning is thrown.
  * Else, an informative error is thrown.
  * An error is also thrown if any variable has two or more processes assigned to it.
  * An error is thrown if any of the given processes are not actually processes, but rather expressions without a LHF-variable.

`processes` is a `Vector` whose elements can be:

1. Any instance of a subtype of [`Process`](@ref). `Process` is like a wrapper around `Equation` that provides some conveniences, e.g., handling of timescales or not having limitations on the left-hand-side (LHS) form.
2. An `Equation`. The LHS format of the equation is limited. Let `x` be a `@variable` and `p` be a `@parameter`. Then, the LHS can only be one of: `x`, `Differential(t)(x)`, `Differential(t)(x)*p`, or `p*Differential(t)(x)`. The versions with `p` may fail unexpectedly. Anything else will error.
3. A `Vector` of the above two, which is then expanded. This allows the convenience of functions representing a physical process that may require many equations to be defined (because e.g., they may introduce more variables).
4. A ModelingToolkit.jl `XDESystem`, in which case the `equations` of the system are expanded as if they were given as a vector of equations like above. This allows the convenience of straightforwardly coupling with already existing `XDESystem`s.

## Default processes

`processes_to_mtkmodel` allows for specifying default processes by giving `default`. These default processes are assigned to variables introduced in the main input `processes`, but themselves do not have an assigned process in the main input.

`default` can be a `Vector` of individual processes (`Equation` or `Process`). Alternatively, `default` can be a `Module`. The recommended way to build field-specific modelling libraries based on ProcessBasedModelling.jl is to define modules/submodules that offer a pool of pre-defined variables and processes. Modules may register their own default processes via the function [`register_default_process!`](@ref). These registered default processes are used when `default` is a `Module`.

## Keyword arguments

  * `type = ODESystem`: the model type to make.
  * `name = nameof(type)`: the name of the model.
  * `independent = t`: the independent variable (default: `@variables t`). `t` is also exported by ProcessBasedModelling.jl for convenience.
  * `warn_default::Bool = true`: if `true`, throw a warning when a variable does not have an assigned process but it has a default value so that it becomes a parameter instead.
  * `check_rhs::Bool = true`: if `true`, check that the RHS of all processes is NOT an `Equation` type. Throw an informative error if there is one. This helps scenarios where the RHS is wrongly an `Equation` assigning the LHS itself (has happened to me many times!).
