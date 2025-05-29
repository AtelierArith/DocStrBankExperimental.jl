```
flatten(obj, [flattentrait::Function], [use::Type], [ignore::Type])
```

Flattening. Flattens a nested struct or tuple to a flat tuple. Query types and flatten trait arguments are optional, but you must pass `use` to pass `ignore`.

# Arguments

  * `obj`: The target type to be reconstructed
  * `flattentrait`: A function returning a Bool, such as a FielMetadata method. With the form: `f(::Type, ::Type{Val{:fieldname}}) = true`
  * `use`: Type or `Union` of types to return in the tuple.
  * `ignore`: Types or `Union` of types  to ignore completly. These are not reurned or recursed over.

# Examples

```jldoctest
julia> using Flatten

julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> foo = Foo(1, 2, 3)
Foo{Int64,Int64,Int64}(1, 2, 3)

julia> flatten(foo)
(1, 2, 3)

julia> nested = Foo(Foo(1, 2, 3), 4.0, 5.0)
Foo{Foo{Int64,Int64,Int64},Float64,Float64}(Foo{Int64,Int64,Int64}(1, 2, 3), 4.0, 5.0)

julia> flatten(nested)
(1, 2, 3, 4.0, 5.0)

To convert the tuple to a vector, simply use [flatten(x)...], or
using static arrays to avoid allocations: `SVector(flatten(x))`.
```

Fields can be excluded from flattening with the `flattenable(struct, field)` method. These are easily defined using `@flattenable` from [FieldMetadata.jl](https://github.com/rafaqz/FieldMetadata.jl), or defining your own custom function with FieldMetadata, or manually with the form:

```julia
julia> import Flatten: flattenable

julia> @flattenable struct Partial{A,B,C}
           a::A | true
           b::B | true
           c::C | false
       end

julia> nestedpartial = Partial(Partial(1.0, 2.0, 3.0), 4, 5)
Partial{Partial{Float64,Float64,Float64},Int64,Int64}(Partial{Float64,Float64,Float64}(1.0, 2.0, 3.0), 4, 5)

julia> nestedpartial = Partial(Partial(1.0, 2.0, 3.0), 4, 5)
Partial{Partial{Float64,Float64,Float64},Int64,Int64}(Partial{Float64,Float64,Float64}(1.0, 2.0, 3.0), 4, 5)

julia> flatten(nestedpartial)
(1.0, 2.0, 4)
```
