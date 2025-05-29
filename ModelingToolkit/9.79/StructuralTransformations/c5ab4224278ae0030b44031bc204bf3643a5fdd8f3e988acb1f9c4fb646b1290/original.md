Main internal function for structural simplification for DAE systems and discrete systems. Generate dummy derivative variables, new equations in terms of variables, return updated system and tearing state.

Terminology and Definition:

A general DAE is in the form of `F(u'(t), u(t), p, t) == 0`. We can characterize variables in `u(t)` into two classes: differential variables (denoted `v(t)`) and algebraic variables (denoted `z(t)`). Differential variables are marked as `SelectedState` and they are differentiated in the DAE system, i.e. `v'(t)` are all the variables in `u'(t)` that actually appear in the system. Algebraic variables are variables that are not differential variables.
