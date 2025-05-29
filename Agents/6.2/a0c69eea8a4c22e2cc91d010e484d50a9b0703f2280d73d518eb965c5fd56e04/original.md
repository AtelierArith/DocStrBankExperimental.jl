```
@agent struct YourAgentType{X}(AgentTypeToInherit) [<: OptionalSupertype]
    extra_property::X
    other_extra_property_with_default::Bool = true
    const other_extra_const_property::Int
    # etc...
end
```

Define an agent struct which includes all fields that `AgentTypeToInherit` has, as well as any additional ones the user may provide. The macro supports all syntaxes that the standard Julia `mutable struct` command allows for, such as `const` field declaration or default values for some fields. Additionally, the resulting type will always have a keyword constructor defined for it (using `@kwdef`).

Using `@agent` is the recommended way to create agent types for Agents.jl.

Structs created with `@agent` by default subtype `AbstractAgent`. They cannot subtype each other, as all structs created from `@agent` are concrete types and `AgentTypeToInherit` itself is also concrete (only concrete types have fields). If you want `YourAgentType` to subtype something other than `AbstractAgent`, use the optional argument `OptionalSupertype` (which itself must then subtype `AbstractAgent`).

## Usage

The macro `@agent` has two primary uses:

1. To include the mandatory fields for a particular space in your agent struct. In this case you would use one of the minimal agent types as `AnotherAgentType`.
2. A convenient way to include fields from another, already existing struct, thereby establishing a toolkit for "type inheritance" in Julia.

The existing minimal agent types are:

  * [`NoSpaceAgent`](@ref)
  * [`GraphAgent`](@ref)
  * [`GridAgent`](@ref)
  * [`ContinuousAgent`](@ref)
  * [`OSMAgent`](@ref)

which describe which fields they will contribute to the new type.

## Examples

### Example without optional hierarchy

Using

```julia
@agent struct Person{T}(GridAgent{2})
    age::Int
    moneyz::T
end
```

will create an agent appropriate for using with 2-dimensional [`GridSpace`](@ref)

```julia
mutable struct Person{T} <: AbstractAgent
    id::Int
    pos::NTuple{2, Int}
    age::Int
    moneyz::T
end
```

Notice that you can also use default values for some fields, in this case you will need to specify the field names with the non-default values

```julia
@agent struct Person2{T}(GridAgent{2})
    age::Int = 30
    moneyz::T
end
# default age value
Person2(id = 1, pos = (1, 1), moneyz = 2000)
# new age value
Person2(1, (1, 1), 40, 2000)
```

### Example with optional hierarchy

An alternative way to make the above structs, that also establishes a user-specific subtyping hierarchy would be to do:

```julia
abstract type AbstractHuman <: AbstractAgent end

@agent struct Worker(GridAgent{2}) <: AbstractHuman
    age::Int
    moneyz::Float64
end

@agent struct Fisher(Worker) <: AbstractHuman
    fish_per_day::Float64
end
```

which would now make both `Fisher` and `Worker` subtypes of `AbstractHuman`.

```julia
julia> supertypes(Fisher)
(Fisher, AbstractHuman, AbstractAgent, Any)

julia> supertypes(Worker)
(Worker, AbstractHuman, AbstractAgent, Any)
```

Note that `Fisher` will *not* be a subtype of `Worker` although `Fisher` has inherited the fields from `Worker`.

### Example highlighting problems with parametric types

Notice that in Julia parametric types are union types. Hence, the following cannot be used:

```julia
@agent struct Dummy{T}(GridAgent{2})
    moneyz::T
end

@agent struct Fisherino{T}(Dummy{T})
    fish_per_day::T
end
```

You will get an error in the definition of `Fisherino`, because the fields of `Dummy{T}` cannot be obtained, because it is a union type. Same with using `Dummy`. You can only use `Dummy{Float64}`.

### Example with common dispatch and no subtyping

It may be that you do not even need to create a subtyping relation if you want to utilize multiple dispatch. Consider the example:

```julia
@agent struct CommonTraits(GridAgent{2})
    age::Int
    speed::Int
    energy::Int
end
```

and then two more structs are made from these traits:

```julia
@agent struct Bird(CommonTraits)
    height::Float64
end

@agent struct Rabbit(CommonTraits)
    underground::Bool
end
```

If you wanted a function that dispatches to both `Rabbit, Bird`, you only have to define:

```julia
Animal = Union{Bird, Rabbit}
f(x::Animal) = ... # uses `CommonTraits` fields
```

However, it should also be said, that there is no real reason here to explicitly type-annotate `x::Animal` in `f`. Don't annotate any type. Annotating a type only becomes useful if there are at least two "abstract" groups, like `Animal, Person`. Then it would make sense to define

```julia
Person = Union{Fisher, Baker}
f(x::Animal) = ... # uses `CommonTraits` fields
f(x::Person) = ... # uses fields that all "persons" have
```

Agents.jl has a convenience function [`add_agent!`](@ref) to create and add agents to the model automatically. In the case you want to create some agents by yourself you can use a constructor accepting the model as first argument so that internal fields, such as the `id`, are set automatically

```julia
model = StandardABM(GridAgent{2}, GridSpace((10,10)))
a = GridAgent{2}(model, (3,4)) # the id is set automatically
```
