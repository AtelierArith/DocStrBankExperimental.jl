```
initialstate = initialize!(model)
```

Return an initial `State` for the model with all dofs set to zero

Modifying a model (invoquing `addnode!` and `addelement!` after `initialize!` will result in an error) 

Optional keyword arguments: `nΛder=1`, `nXder=1`, `nUder=1` to specify the number of "derivatives" to store in the `State`.   note that "`n⋅der==order+1`", that is, for a dynamic problem (with accelerations), `nXder=3` so that   `order==2`.  Setting  `n⋅der` is only required if [`setdof!`](@ref) will be used.  A dynamic solver   handles a "static" initial state perfectly well. `time=-∞` the time associated to the initial state.  Note that for example setting `time=0.`, and then calling a solver with a first time step also at `0.` causes an error.  

See also: [`setdof!`](@ref), [`Model`](@ref), [`addnode!`](@ref), [`addelement!`](@ref), [`solve`](@ref)
