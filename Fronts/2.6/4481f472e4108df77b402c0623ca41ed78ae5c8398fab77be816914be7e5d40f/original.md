Solution to a problem.

```
(::Solution)(r, t)
(::Solution)(o)
```

Evaluate the solution.

# Properties

  * `retcode`: termination status of the solver. See [`ReturnCode`](https://docs.sciml.ai/SciMLBase/stable/interfaces/Solutions/#retcodes).
  * `i`: initial value.
  * `b`: boundary value.
  * `d_dob`: `o`-derivative at the boundary, where `o` is the Boltzmann variable. See also [`o`](@ref).
  * `ob`: boundary constant. See also [`rb`](@ref).
  * `oi`: for `o≥oi`, the solution evaluates to the initial value.
  * `prob`: problem solved.
  * `alg`: algorithm used.
  * `original`: original solution object, if applicable.
