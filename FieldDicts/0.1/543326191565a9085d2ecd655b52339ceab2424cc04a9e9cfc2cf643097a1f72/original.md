```
FieldDict{V}(x) <: AbstractDict{Symbol,V}
```

Wraps `x` and provides access to its fields through a dictionary interface. The resulting key value pairs correspond to `x`'s field names and respective values.

# Examples

```jldoctest fielddict_docstring
julia> using FieldDicts

julia> mutable struct Foo
           x::Int
           y::Float64
       end

julia> x = Foo(1, 2);

julia> d = FieldDict(x)
FieldDict{Real, Foo} with 2 entries:
  :x => 1
  :y => 2.0

```

The keys and properties are the same as the underlying structures field names.

```jldoctest fielddict_docstring
julia> keys(d) == propertynames(d) == (:x, :y)
true

```

The values are similarly accessible through the dictionary interface.

```jldoctest fielddict_docstring
julia> collect(values(d)) == [1, 2]
true

```

These fields can be accessed via traditional dictionary-like access or the dot-property notation.

```jldoctest fielddict_docstring
julia> d[:x] = 1;

julia> d.x == d[:x] == 1
true

julia> get(d, :y, 3)
2.0

julia> get(d, :z, 3)
3

```
