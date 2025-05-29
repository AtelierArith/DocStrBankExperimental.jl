```
reparametrize_global(ode, options...)
```

Finds a reparametrization of `ode` in terms of globally identifiabile functions.

Returns a tuple (`new_ode`, `new_vars`, `implicit_relations`), such that:

  * `new_ode` is the reparametrized ODE system
  * `new_vars` is a mapping from the new variables to the original ones
  * `relations` is the array of implicit algebraic relations among `new_vars`. Usually, `relations` is empty.

## Options

The function accepts the following optional arguments.

  * `seed`: A float in the range from 0 to 1, random seed (default is `seed = 42`).
  * `prob_threshold`: The probability of correctness (default is `prob_threshold = 0.99`).

## Example

```jldoctest
using StructuralIdentifiability

ode = @ODEmodel(
    x1'(t) = a * x1(t) - b*x1(t)*x2(t),
    x2'(t) = -c * x2(t) + d*x1(t)*x2(t),
    y(t) = x1(t)
)

new_ode, new_vars, relations = reparametrize_global(ode)
```

Then, we have the following:

```
# new_ode
X2'(t) = X1(t)*X2(t)*a2 - X2(t)*a1
X1'(t) = -X1(t)*X2(t) + X1(t)*a3
y1(t) = X1(t)

# new_vars
Dict{Nemo.QQMPolyRingElem, AbstractAlgebra.Generic.FracFieldElem{Nemo.QQMPolyRingElem}} with 6 entries:
  X2 => b*x2
  y1 => y
  X1 => x1
  a2 => d
  a3 => a
  a1 => c
```

Notice that the `new_ode` is fully identifiabile, and has `1` less parameter compared to the original one.
