```
port(type::Symbol, place::Place)
```

Creates a port connecting to the given place with respect to the arc type. Note: the allowed port types are one of the following:     :in, :out, :inout

# Examples

```julia-repl
julia> p1 = place("input1", :string)
Place "input1" created.


julia> port(:in, p1)
A port of type "in" connected to place "input1".

```

See also [`place`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref).
