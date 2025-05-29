```
Lens
```

A `Lens` allows to access or replace deeply nested parts of complicated objects.

# Example

```jldoctest
julia> using Setfield

julia> struct T;a;b; end

julia> obj = T("AA", "BB")
T("AA", "BB")

julia> lens = @lens _.a
(@lens _.a)

julia> get(obj, lens)
"AA"

julia> set(obj, lens, 2)
T(2, "BB")

julia> obj
T("AA", "BB")

julia> modify(lowercase, obj, lens)
T("aa", "BB")
```

# Interface

Concrete subtypes of `Lens` have to implement

  * `set(obj, lens, val)`
  * `get(obj, lens)`

These must be pure functions, that satisfy the three lens laws:

```jldoctest; output = false, setup = :(using Setfield; (≅ = (==)); obj = (a="A", b="B"); lens = @lens _.a; val = 2; val1 = 10; val2 = 20)
@assert get(set(obj, lens, val), lens) ≅ val
        # You get what you set.
@assert set(obj, lens, get(obj, lens)) ≅ obj
        # Setting what was already there changes nothing.
@assert set(set(obj, lens, val1), lens, val2) ≅ set(obj, lens, val2)
        # The last set wins.

# output

```

Here `≅` is an appropriate notion of equality or an approximation of it. In most contexts this is simply `==`. But in some contexts it might be `===`, `≈`, `isequal` or something else instead. For instance `==` does not work in `Float64` context, because `get(set(obj, lens, NaN), lens) == NaN` can never hold. Instead `isequal` or `≅(x::Float64, y::Float64) = isequal(x,y) | x ≈ y` are possible alternatives.

See also [`@lens`](@ref), [`set`](@ref), [`get`](@ref), [`modify`](@ref).
