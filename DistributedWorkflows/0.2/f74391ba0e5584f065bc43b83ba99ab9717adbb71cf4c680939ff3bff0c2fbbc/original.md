```
place(name::String)
place(name::String, type::Symbol)
```

Creates an object of type Place for the Petri net object. Note: acceptable place types are:   :string, :control, :control_init, :counter

Also, note that an input or output place cannot be of type :control.

# Examples

```julia-repl
julia> place("new_place", :string)
Place "new_place" created.

julia> place("in_place", :control)
Place "in_place" with control token created.
```

See also [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref).
