```
setscale!(model;scale=nothing,Λscale=nothing)
```

Provide scale value for each type (class and field) of dof in the model.   This is usued to improve the conditioning of the incremental problems and for convergence criteria. `scale` is a `NamedTuple` with fieldnames within  `X`, `U` and `A`.  Each field is itself a `NamedTuple` with fieldnames being dof fields, and value being the expected order of magnitude.

For example `scale = (X=(tx=10,rx=1),A=(drag=3.))` should be read as: X-dofs of field `:tx` are expected to be of the order of magnitude of 10m in the solution, `:rx` to be of the order of 1 radian, and A-dofs of field `drag` of the order of 3.  All other degrees of freedom are of the order of 1.

Determining scaling coefficients that improve the condition number of incremental matrices is a hard problem.

`Λscale` is a scalar. The scale of a Λ-dof will be deemed to be the scale of the  corresponding X-dof, times `Λscale`.

See also: [`addnode!`](@ref), [`describe`](@ref), [`coord`](@ref), [`studyscale`](@ref)
