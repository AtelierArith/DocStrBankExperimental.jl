```
@private_struct ...
```

Annotates a struct with particular `@private` fields. These fields cannot be accessed     directly with the dot-syntax (`a.b`) in normal use. Instead, the struct fields     should be interacted with indirectly through `@private_method` methods     which have privileged access to the fields of the struct.

Calling `getfield` on the struct directly is still functional, but by default `getproperty`     will call a progammatically-generated `PrivateFields.jl` method which verifies     field privacy. 

If you wish to overload the struct with a custom `getproperty` method while preserving      field privacy, you should instead implement [`getproperty_direct`](@ref) from `PrivateFields.jl`

# Usage

Prepend `@private` before field definitions of your struct to tag those fields as private.  Private/public fields can be declared in any order.

See the example below.

# Example

```
@private_struct Foo{X,Y}
    @private x::X
    y::Y
end
```
