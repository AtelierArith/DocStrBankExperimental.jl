```
update!(obj, data, [flattentrait::Function], [use::Type], [ignore::Type])
```

Update a mutable object with a `Tuple` or `Vector` of data. Query types and flatten trait arguments are optional, but you must pass `use` to pass `ignore`.

# Arguments

  * `obj`: The target type to be reconstructed
  * `data`: Replacement data - an `AbstractArray`, `Tuple` or type that defines `getfield`.
  * `flattentrait`: A function returning a Bool, such as a FielMetadat method. With the form: `f(::Type, ::Type{Val{:fieldname}}) = true`
  * `use`: Types to return in the tuple.
  * `ignore`: Types to ignore completly. These are not reurned or recursed over.

# Examples

```jldoctest
julia> using Flatten

julia> mutable struct MutableFoo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> mufoo = MutableFoo(1, 2, 3)
MutableFoo{Int64,Int64,Int64}(1, 2, 3)

julia> update!(mufoo, (2, 4, 6))
MutableFoo{Int64,Int64,Int64}(2, 4, 6)

julia> mufoo = MutableFoo(1, 2, :three)
MutableFoo{Int64,Int64,Symbol}(1, 2, :three)

julia> update!(mufoo, (:foo,), Symbol)
MutableFoo{Int64,Int64,Symbol}(1, 2, :foo)
```
