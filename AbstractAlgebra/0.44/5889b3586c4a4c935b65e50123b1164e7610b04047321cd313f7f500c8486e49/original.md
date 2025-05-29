```
@attributes typedef
```

This is a helper macro that ensures that there is storage for attributes in the type declared in the expression `typedef`, which must be either a `mutable struct` definition expression, or the name of a `mutable struct` type.

The latter variant is useful to enable attribute storage for types defined in other packages. Note that `@attributes` is idempotent: when applied to a type for which attribute storage is already available, it does nothing.

For singleton types, attribute storage is also supported, and in fact always enabled. Thus it is not necessary to apply this macro to such a type.

!!! note
    When applied to a struct definition this macro adds a new field to the struct. For structs without constructor, this will change the signature of the default inner constructor, which requires explicit values for every field, including the attribute storage field this macro adds. Usually it is thus preferable to add an explicit default constructor, as in the example below.


# Examples

Applying the macro to a struct definition results in internal storage of the attributes:

```jldoctest
julia> @attributes mutable struct MyGroup
           order::Int
           MyGroup(order::Int) = new(order)
       end

julia> G = MyGroup(5)
MyGroup(5, #undef)

julia> set_attribute!(G, :isfinite, :true)

julia> get_attribute(G, :isfinite)
true
```

Applying the macro to a typename results in external storage of the attributes:

```jldoctest
julia> mutable struct MyOtherGroup
           order::Int
           MyOtherGroup(order::Int) = new(order)
       end

julia> @attributes MyOtherGroup

julia> G = MyOtherGroup(5)
MyOtherGroup(5)

julia> set_attribute!(G, :isfinite, :true)

julia> get_attribute(G, :isfinite)
true
```
