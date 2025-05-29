```
@aagent [OptionalBasetype=FreeAgent] [OptionalSupertype=AbstractAlgebraicAgent] struct my_agent
    extra_fields...
end
```

Define a custom agent type, and include fields expected by default interface methods (see [`FreeAgent`](@ref)).

Fields are mutable by default, but can be declared immutable using `const` keyword.

Provides a constructor which takes agent's name at the input, and populates the common fields.

# Example

```julia
@aagent struct Molecule
    age::Float64
    birth_time::Float64
    sales::Float64
end
```

Optional base type:

```julia
@aagent FreeAgent struct Molecule
    age::Float64
    birth_time::Float64
    sales::Float64
end
```

Optional base type and a super type:

```julia
@aagent FreeAgent AbstractMolecule struct Molecule
    age::Float64
    birth_time::Float64
    sales::Float64
end
```

Parametric types:

```julia
@aagent struct MyAgent{T <: Real, P <: Real}
    field1::T
    field2::P
end

MyAgent{Float64, Int}("myagent", 1, 2)
```
