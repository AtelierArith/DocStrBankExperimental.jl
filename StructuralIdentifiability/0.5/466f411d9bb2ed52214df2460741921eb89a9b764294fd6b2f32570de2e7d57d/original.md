```
find_identifiable_functions(ode::ODE; options...)
```

Finds all functions of parameters/states that are identifiable in the given ODE system.

## Options

This functions takes the following optional arguments:

  * `with_states`: When `true`, also reports the identifiabile functions in the   ODE states. Default is `false`.
  * `simplify`: The extent to which the output functions are simplified. Stronger simplification may require more time. Possible options are:

      * `:standard`: Default simplification.
      * `:weak`: Weak simplification. This option is the fastest, but the output functions can be quite complex.
      * `:strong`: Strong simplification. This option is the slowest, but the output

    functions are nice and simple.

      * `:absent`: No simplification.
  * `known_ic`: a list of functions whose initial conditions are assumed to be known, then the returned identifiable functions will be functions of parameters and initial conditions, not states (this is an experimental functionality).
  * `prob_threshold`: A float in the range from 0 to 1, the probability of correctness. Default is `0.99`.
  * `seed`: The rng seed. Default value is `42`.
  * `loglevel` - the minimal level of log messages to display (`Logging.Info` by default)

## Example

```jldoctest
using StructuralIdentifiability

ode = @ODEmodel(
    x0'(t) = -(a01 + a21) * x0(t) + a12 * x1(t),
    x1'(t) = a21 * x0(t) - a12 * x1(t),
    y(t) = x0(t)
)

find_identifiable_functions(ode)

# prints
3-element Vector{AbstractAlgebra.Generic.FracFieldElem{Nemo.QQMPolyRingElem}}:
 a12 + a01 + a21
 a12*a01
```
