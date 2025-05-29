```
@steadystate model [type] lhs = rhs
@steadystate model begin
    lhs = rhs
    @delete _SSEQ1 _SSEQ2
    @level lhs = rhs
    @slope lhs = rhs
end
@steadystate model @delete _SSEQ1 _SSEQ2
```

Add a steady state equation to the model.

The steady state system of the model is automatically derived from the dynamic system. Use this macro to define additional equations for the steady state. This is particularly useful in the case of a non-linear model that might have multiple steady state, or the steady state might be difficult to solve for, to help the steady state solver find the one you want to use.

  * `model` is the model instance you want to update
  * `type` (optional) is the type of constraint you want to add. This can be `level`

or `slope`. If missing, the default is `level`

  * `lhs = rhs` is the expression defining the steady state constraint. In the

equation, use variables and shocks from the model, but without any t-references.

There is also a block form of this which allows for several steadystate equations.   These can be preceeded by @level or @slope to specify the type. @level is the default.   Steadystate equations can also be removed with @delete lines followed by a list of constraint keys.
