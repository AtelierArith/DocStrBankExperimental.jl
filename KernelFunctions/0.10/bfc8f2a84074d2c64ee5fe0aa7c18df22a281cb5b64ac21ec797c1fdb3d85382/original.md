```
SelectTransform(dims)
```

Transformation that selects the dimensions `dims` of the input.

# Examples

```jldoctest
julia> dims = [1, 3, 5, 6, 7]; t = SelectTransform(dims); X = rand(100, 10);

julia> map(t, ColVecs(X)) == ColVecs(X[dims, :])
true
```
