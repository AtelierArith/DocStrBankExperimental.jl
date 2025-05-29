The `@agent` macro is used to define a Fjage agent. The macro takes in a `struct` definition and converts it into an agent definition. The fields in the struct are treated as agent attributes. Fjage agent types are subtypes of `Fjage.Agent` and are mutable.

The `struct` definition may include initialization, as supported by the `Base.@kwdef` macro.

# Examples:

```julia
using Fjage

@agent struct MyAgent
  field1::Int = 1
  field2::String = "hello"
end

abstract type SpecialAgent <: Fjage.Agent end

@agent struct MySpecialAgent <: SpecialAgent
  agentnumber::Int = 007
  licensedtokill::Bool = true
end
```
