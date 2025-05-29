```
lgl_deref(solver::LglPtr, lit::Integer)::Cint
```

After 'lgl_sat' was called and returned `Lingeling.SATISFIABLE`, then the satisfying assignment can be obtained by 'dereferencing' literals. The value of the literal is return as `1` for true,  `-1` for false and `0` for an unknown value.

# Arguments

  * `solver::LglPtr`: A pointer to the Lingeling SAT-Solver.
  * `lit::Integer`: The literal to dereference.

# Returns

  * `val::Cint`: The value of the literal. `1` for true, `-1` for false, `0` for unknown.

# Throws

  * `InexactError`: If the literal can not be converted to a `Cint`.
