```
@enum VariableFunction
```

Allowed values of `:vfunction` Variable [`Attribute`](@ref),  defining the Variable function to the host ODE or DAE solver.

Explicit ODE problems with dS/dt = F(S) consist of pairs of S::VF*StateExplicit, F::VF*Deriv Variables.

An implicit ODE problem with dU/dt = F(U) where Total variables U are functions U(S) of State variables S will consist of pairs of U::VF*Total and F::VF*Deriv Variables, and also the same number of S::VF_StateTotal (in  no particular order).

Algebraic constraints  C(S) = 0 include variables C::VF*Constraint and the same number of S::VF*State, with no corresponding VF_Deriv.

Not all solvers support all combinations.
