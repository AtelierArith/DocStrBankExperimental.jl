```
Name(name)
```

Create a typed `Name`. Inverse of [`unname`](@ref). See also [`@name_str`](@ref).

```jldoctest name
julia> using LightQuery


julia> Name(:a)
name"a"
```

`Name`s can be used as selector functions.

```jldoctest name
julia> using Test: @inferred


julia> data = (a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0)
(a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0)

julia> @inferred name"c"(data)
1
```

Multiple names can be used as selector functions

```jldoctest name
julia> @inferred (name"c", name"f")(data)
(c = 1, f = 1.0)
```

A final use for names can be as a way to construct NamedTuples from pairs. Using `Name`s instead of `Symbol`s gives type stability.

```jldoctest name
julia> @inferred NamedTuple((name"a", 1), (name"b", 2))
(a = 1, b = 2)
```
