```
reconstruct(obj, data, [flattentrait::Function], [use::Type], [ignore::Type])
```

Reconstruct an object from Tuple or Vector data and an existing object. Data should be at least as long as the queried fields in the obj. Query types and flatten trait arguments are optional, but you must pass `use` to pass `ignore`.

# Arguments

  * `obj`: The target type to be reconstructed
  * `data`: Replacement data - an `AbstractArray`, `Tuple` or type that defines `getfield`.
  * `flattentrait`: A function returning a Bool, such as a FielMetadata method. With the form: `f(::Type, ::Type{Val{:fieldname}}) = true`
  * `use`: Type or `Union` of types to return in the tuple.
  * `ignore`: Types or `Union` of types  to ignore completly. These are not reurned or recursed over.

# Examples

```julia
julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> reconstruct(Foo(1, 2, 3), (1, :two, 3.0))
Foo{Int64,Symbol,Float64}(1, :two, 3.0)
```
