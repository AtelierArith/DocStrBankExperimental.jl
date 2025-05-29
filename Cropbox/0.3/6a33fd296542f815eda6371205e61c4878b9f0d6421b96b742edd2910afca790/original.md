```
parameters(S; <keyword arguments>) -> Config
```

Extract a list of parameters defined for system `S`.

# Arguments

  * `S::Type{<:System}`: type of system to be inspected.

# Keyword Arguments

  * `alias=false`: show alias instead of parameter name.
  * `recursive=false`: extract parameters from other systems declared in `S`.
  * `exclude=()`: systems excluded in recurisve search.
  * `scope=nothing`: evaluation scope; default is `S.name.module`.

# Examples

```julia-repl
julia> @system S(Controller) begin
           a: aaa => 1 ~ preserve(parameter)
       end;

julia> parameters(S)
Config for 1 system:
  S
    a = 1

julia> parameters(S; alias=true)
Config for 1 system:
  S
    aaa = 1

julia> parameters(S; recursive=true)
Config for 3 systems:
  Clock
    init = 0 hr
    step = 1 hr
  Context
  S
    a = 1

julia> parameters(S; recursive=true, exclude=(Context,))
Config for 1 system:
  S
    a = 1
```
