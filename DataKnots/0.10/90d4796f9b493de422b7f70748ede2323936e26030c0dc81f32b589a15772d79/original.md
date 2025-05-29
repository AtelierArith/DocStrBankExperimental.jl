```
Lift(f, (X₁, X₂ … Xₙ)) :: Query
```

`Lift` lets you use a function as a query combinator.

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> Lift(+, (It.x, It.y))]
┼───┼
│ 3 │
```

`Lift` is implicitly used when a function is broadcast over queries.

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> (It.x .+ It.y)]
┼───┼
│ 3 │
```

Functions accepting a `AbstractVector` can be used with plural queries.

```jldoctest
julia> unitknot[sum.(Lift(1:3))]
┼───┼
│ 6 │
```

Functions returning `AbstractVector` become plural queries.

```jldoctest
julia> unitknot[Lift((x='a', y='c')) >> Lift(:, (It.x, It.y))]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```
