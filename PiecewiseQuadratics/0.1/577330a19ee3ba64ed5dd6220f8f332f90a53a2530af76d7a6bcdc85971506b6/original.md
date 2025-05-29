```
sum(f_list::Vector{BoundedQuadratic})
```

Return the BoundedQuadratic sum of a list of BoundedQuadratics if it is valid, else `nothing`.

# Example

```jldoctest
julia> bq = BoundedQuadratic(-1., 5., 1., 2., 3.)
BoundedQuadratic: f(x) = 1.00000 x² + 2.00000 x + 3.00000, ∀x ∈ [-1.00000, 5.00000]

julia> sum([bq, bq])
BoundedQuadratic: f(x) = 2.00000 x² + 4.00000 x + 6.00000, ∀x ∈ [-1.00000, 5.00000]

```
