```
rightif(predicate, [focus = identity]) -> op::Function
```

Return a binary function that keeps the first argument unless `predicate` evaluates to `true`.

This is equivalent to

```julia
(l, r) -> predicate(focus(l), focus(r)) ? r : l
```

# Examples

```jldoctest
julia> using DataTools, Transducers

julia> table = 1:100 |> Map(x -> (k = gcd(x, 42), v = x));

julia> table |> Take(5) |> collect  # preview
5-element Array{NamedTuple{(:k, :v),Tuple{Int64,Int64}},1}:
 (k = 1, v = 1)
 (k = 2, v = 2)
 (k = 3, v = 3)
 (k = 2, v = 4)
 (k = 1, v = 5)

julia> foldl(rightif(<), Map(x -> x.k), table)  # maximum
42

julia> foldl(rightif(>), Map(x -> x.k), table)  # minimum
1

julia> foldl(rightif(<, x -> x.k), table)   # first maximum
(k = 42, v = 42)

julia> foldl(rightif(<=, x -> x.k), table)  # last maximum
(k = 42, v = 84)

julia> foldl(rightif(>, x -> x.k), table)   # first minimum
(k = 1, v = 1)

julia> foldl(rightif(>=, x -> x.k), table)  # last minimum
(k = 1, v = 97)

julia> table |> Scan(rightif(<, x -> x.k)) |> Take(5) |> collect
5-element Array{NamedTuple{(:k, :v),Tuple{Int64,Int64}},1}:
 (k = 1, v = 1)
 (k = 2, v = 2)
 (k = 3, v = 3)
 (k = 3, v = 3)
 (k = 3, v = 3)
```
