@protostruct(struct_ [, prefix_])

creates a struct that can have structure inherited from it and can inherit structure.

additionally it creates an abstract type with a name given by the struct definitions name and a prefix. The concrete type inherits from the abstract type and anything which inherits the concrete types structure also inherits behavior from the abstract type.

```Julia
julia> using StructuralInheritance

julia> @protostruct struct A{T}
           fieldFromA::T
       end
ProtoA

julia> @protostruct struct B{D} <: A{Complex{D}}
          fieldFromB::D
       end "SomeOtherPrefix"
SomeOtherPrefixB

julia> @protostruct struct C <: B{Int}
         fieldFromC
       end
ProtoC
```
