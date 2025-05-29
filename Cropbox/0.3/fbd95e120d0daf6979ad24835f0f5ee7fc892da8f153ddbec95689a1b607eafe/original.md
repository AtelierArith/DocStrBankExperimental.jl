```
parameters(s; <keyword arguments>) -> Config
```

Extract a list of parameters from an existing instance of system `s`.

# Arguments

  * `s::System`: instance of system to be inspected.

# Keyword Arguments

  * `alias=false`: show alias instead of parameter name.
  * `recursive=false`: extract parameters from other systems declared in `S`.
  * `exclude=()`: systems excluded in recurisve search.

# Examples

```julia-repl
julia> @system S(Controller) begin
           a: aaa => 1 ~ preserve(parameter)
       end;

julia> s = instance(S; config = :S => :a => 2);

julia> parameters(s)
Config for 1 system:
  S
    a = 2.0

julia> parameters(s; alias = true)
Config for 1 system:
  S
    aaa = 2.0

julia> parameters(s; recursive = true)
Config for 3 systems:
  Clock
    init = 0.0 hr
    step = 1.0 hr
  Context
  S
    a = 2.0

julia> parameters(s; recursive = true, exclude = (Context,))
Config for 1 system:
  S
    a = 2.0
```
