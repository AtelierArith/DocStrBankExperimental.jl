```
@system name[{patches..}][(mixins..)] [<: type] [decl] -> Type{<:System}
```

Declare a new system called `name` with new variables declared in `decl` block using a custom syntax. The resultant system is subtype of `System` or a custom `type`. `mixins` allows reusing specification of existing systems to be pasted into the declaration of new system. `patches` may provide type substitution and/or constant definition needed for advanced use.

# Variable

```
name[(args..; kwargs..)][: alias] [=> expr] [~ [state][::type|<:type][(tags..)]]
```

  * `name`: variable name; usually short abbreviation.
  * `args`: automatically bound depending variables
  * `kwargs`: custom bound depending variables; used by `call` and `integrate`.
  * `alias`: alternative name; long description.
  * `expr`: state-specific code snippet; use begin-end block for multiple statements.
  * `type`: internal data type; default is Float64 for many, but not all, variables.
  * `tags`: state-specific options; `unit`, `min`/`max`, etc.

# States

  * `hold`: marks a placeholder for variable shared between mixins.
  * `wrap`: passes a state variable to other fucnction as is with no unwrapping its value.
  * `advance`: manages a time-keeping variable; `time` and `tick` from `Clock`.
  * `preserve`: keeps initially assigned value with no further updates; constants, parameters.
  * `tabulate`: makes a two dimensional table with named keys; *i.e.* partitioning table.
  * `interpolate`: makes a curve function interpolated with discrete values; *i.e.* soil characteristic curve.
  * `track`: evaluates variable expression as is for each update.
  * `remember`: keeps tracking variable until a certain condition is met; essentially `track` turning into `preserve`.
  * `provide`: manages a table of time-series in DataFrame.
  * `drive`: fetches the current value from a time-series; maybe supplied by `provide`.
  * `call`: defines a partial function bound with some variables.
  * `integrate`: calculates integral using Gaussian method; not for time domain.
  * `accumulate`: emulates integration of rate variable over time; essentially Euler method.
  * `capture`: calculates difference between integration for each time step.
  * `flag`: sets a boolean flag; essentially `track::Bool`.
  * `produce`: attaches a new instance of system dynamically constructed; *i.e.* root structure growth.
  * `bisect`: solves nonlinear equation using bisection method; *i.e.* gas-exchange model coupling.
  * `solve`: solves polynomial equation symbolically; *i.e.* quadratic equations in photosynthesis model.

# Examples

```julia-repl
julia> @system S(Controller) begin
           a => 1 ~ preserve(parameter)
           b(a) ~ accumulate
       end
S
```
