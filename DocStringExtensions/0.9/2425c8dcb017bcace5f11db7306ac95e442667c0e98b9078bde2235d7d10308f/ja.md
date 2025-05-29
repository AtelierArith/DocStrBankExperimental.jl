An [`Abbreviation`](@ref) for including a summary of the signature of a type definition. Some of the following information may be included in the output:

  * whether the object is an `abstract` type or a `bitstype`;
  * mutability (either `type` or `struct` is printed);
  * the unqualified name of the type;
  * any type parameters;
  * the supertype of the type if it is not `Any`.

# Examples

The generated output for a type definition such as:

```julia
"""
$(TYPEDEF)
"""
struct MyType{S, T <: Integer} <: AbstractArray
    # ...
end
```

will look similar to the following:

````markdown
```julia
struct MyType{S, T<:Integer} <: AbstractArray
```
````

!!! note
    No information about the fields of the type is printed. Use the [`FIELDS`](@ref) abbreviation to include information about the fields of a type.

