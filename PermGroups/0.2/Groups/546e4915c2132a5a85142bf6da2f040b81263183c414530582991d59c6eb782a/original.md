`@GapObj struct...`

A `GapObj` is a kind of object where properties are computed on demand when asked  for.  So  it  has  fixed  fields  but can dynamically have new ones. Accessing  fixed  fields  is  as  efficient  as  a  field  of any `struct`. Accessing a dynamic field takes the time of a `Dict` lookup.

```julia_repl
julia> @GapObj struct Foo
       a::Int
       end

julia> s=Foo(1,Dict{Symbol,Any}())
Foo(1, Dict{Symbol, Any}())

julia> s.a
1

julia> haskey(s,:b)
false

julia> s.b="hello"
"hello"

julia> haskey(s,:b)
true

julia> s.b
"hello"
```

The dynamic fields are stored in the field `.prop` of `G`, which is of type `Dict{Symbol,  Any}()`.  This  explains  the  extra  argument needed in the constructor.  The name is because it mimics a GAP record, but perhaps there could be a better name. The methods the `GapObj` inherits from its field `prop` are `haskey`, `getindex`, `delete!` and `get!`.
