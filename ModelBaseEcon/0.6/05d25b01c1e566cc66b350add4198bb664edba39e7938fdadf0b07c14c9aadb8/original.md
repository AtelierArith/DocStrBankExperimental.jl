```
struct ModelVariable ⋯ end
```

Data type for model variables. `ModelVariable` functions like a `Symbol` in many respects, but also holds meta-information about the variable, such as doc string, the variable type, transformation, steady state behaviour.

Variable types include

  * `:var` - a regular variable is endogenous by default, but can be exogenized.
  * `:shock` - a shock variable is exogenous by default, but can be endogenized. Steady state is 0.
  * `:exog` - an exogenous variable is always exogenous.

These can be declared with [`@variables`](@ref), [`@shocks`](@ref), and  [`@exogenous`](@ref) blocks. You can also use `@exog` within an  `@variables` block to declare an exogenous variable.

Transformations include

  * `:none` - no transformation. This is the default. In steady state these variables exhibit linear growth.
  * `:log` - logarithm. This is useful for variables that must be always strictly positive. Internally the solver work with the logarithm of the variable. in steady state these variables exhibit exponential growth (the log variable grows linearly).
  * `:neglog` - same as `:log` but for variables that are strictly negative.

These can be declared with [`@logvariables`](@ref), [`@neglogvariables`](@ref), `@log`, `@neglog`.

Steady state behaviours include

  * `:const` - these variables have zero slope in steady state and final conditions.
  * `:growth` - these variables have constant slope in steady state and final conditions. The meaning of "slope" changes depending on the transformation. For `:log` and `:neglog` variables this is the growth rate, while for `:none` variables it is the usual slope of linear growth.

Shock variables are always `:const` while regular variables are assumed `:growth`. They can be declared `:const` using `@steady`.
