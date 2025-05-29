```
ComponentCondition(f::Function, sym, psym)
```

Creates a callback condition for a [`ComponentCallback`].

  * `f`: The condition function. Must be a function of the form `out=f(u, p, t)` when used for [`ContinousComponentCallback`](@ref) or [`DiscreteComponentCallback`](@ref) and `f!(out, u, p, t)` when used for [`VectorContinousComponentCallback`](@ref).

      * Arguments of `f`

          * `u`: The current value of the selecte `sym` states, provided as a [`SymbolicView`](@ref) object.
          * `p`: The current value of the selected `psym` parameters.
          * `t`: The current simulation time.
  * `sym`: A vector or tuple of symbols, which represent **states** (including inputs, outputs, observed) of the component model. Determines, which states will be available thorugh parameter `u` in the callback condition function `f`.
  * `psym`: A vector or tuple of symbols, which represetn **parameters** of the component mode. Determines, which parameters will be available in the condition function `f`

# Example

Consider a component model with states `[:u1, :u2]`, inputs `[:i]`, outputs `[:o]` and parameters `[:p1, :p2]`.

```
ComponentCondition([:u1, :o], [:p1]) do u, p, t
    # access states symbolicially or via int index
    u[:u1] == u[1]
    u[:o] == u[2]
    p[:p1] == p[1]
    # the states/prameters `:u2`, `:i` and `:p2` are not available as
    # they are not listed in the `sym` and `psym` arguments.
end
```
