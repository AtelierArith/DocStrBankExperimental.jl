```
abstract type TransientIMEXFEOperator <: TransientFEOperator end
```

Implicit-Explicit decomposition of a residual defining a `TransientFEOperator`:

```
residual(t, u, v) = implicit_residual(t, u, v)
                  + explicit_residual(t, u, v),
```

where

  * The implicit operator defined by the implicit residual is considered stiff and is meant to be solved implicitly,
  * The explicit operator defined by the explicit residual is considered non-stiff and is meant to be solved explicitly.
  * Both the implicit and explicit residuals are linear in `v`.

# Important

The explicit operator must have one order less than the implicit operator, so that the mass term of the global operator is fully contained in the implicit operator.

# Mandatory

  * [`get_imex_operators(tfeop)`](@ref)

# Optional

  * [`get_test(tfeop)`](@ref)
  * [`get_trial(tfeop)`](@ref)
  * [`get_algebraic_operator(tfeop)`](@ref)
