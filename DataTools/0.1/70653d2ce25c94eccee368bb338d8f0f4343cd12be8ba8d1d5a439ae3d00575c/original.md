```
oncol(iname₁ => spec₁, ..., inameₙ => specₙ) -> f::Function
oncol(; $iname₁ = spec₁, ..., $inameₙ = specₙ) -> f::Function
```

Combine functions that work on a column and create a function that work on an entire row.

It constructs a reducing step function acting on a table row where `specᵢ` is either a reducing step function or a `Pair` of a reducing step function and an output column name.

It also defines a unary function when `specᵢ` is either a unary function or a `Pair` of a unary function and an output column name.

This function is inspired by the "`Pair` notation" in DataFrames.jl (see also [Split-apply-combine · DataFrames.jl](https://juliadata.github.io/DataFrames.jl/stable/man/split_apply_combine/) and [`DataFrames.select`](https://juliadata.github.io/DataFrames.jl/stable/lib/functions/#DataFrames.select)).

# Examples

```jldoctest oncol
julia> using DataTools
       using Transducers

julia> rf = oncol(a = +, b = *);

julia> foldl(rf, Map(identity), [(a = 1, b = 2), (a = 3, b = 4)])
(a = 4, b = 8)

julia> rf((a = 1, b = 2), (a = 3, b = 4))
(a = 4, b = 8)

julia> rf = oncol(:a => (+) => :sum, :a => max => :max);

julia> foldl(rf, Map(identity), [(a = 1,), (a = 2,)])
(sum = 3, max = 2)

julia> rf((sum = 1, max = 1), (a = 2,))
(sum = 3, max = 2)

julia> rf = oncol(:a => min, :a => max);

julia> foldl(rf, Map(identity), [(a = 2,), (a = 1,)])
(a_min = 1, a_max = 2)

julia> rf((a_min = 2, a_max = 2), (a = 1,))
(a_min = 1, a_max = 2)

julia> foldl(rf, Map(x -> (a = x,)), [5, 2, 6, 8, 3])
(a_min = 2, a_max = 8)
```

`oncol` also defines a unary function

```jldoctest oncol
julia> f = oncol(a = string);

julia> f((a = 1, b = 2))
(a = "1",)
```

Note that `oncol` does not verify the arity of input functions.  If the input functions have unary and binary methods, `oncol` is callable with both arities:

```jldoctest oncol
julia> f((a = 1, b = 2), (a = 3, b = 4))
(a = "13",)
```
