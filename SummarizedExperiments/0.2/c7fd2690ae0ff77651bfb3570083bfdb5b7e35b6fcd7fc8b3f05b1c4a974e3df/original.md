```
setassay!(x[, i], value)
```

Set the requested assay in `x` to any array-like `value`. The first two dimensions of `value` must have extent equal to those of `x`.

`i` may be an integer specifying an index, in which case it must be positive and no greater than `length(assays(x))`; or a string containing the name, in which case it may be an existing or new name. If `i` is not supplied, `value` is set as the first assay of `x`.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> first_sum = sum(assay(x));

julia> second_sum = sum(assay(x, 2));

julia> setassay!(x, assay(x, 2)); # Replacing the first assay with the second.

julia> first_sum == sum(assay(x))
false

julia> second_sum == sum(assay(x))
true

julia> setassay!(x, 1, assay(x, 2)); # More explicit forms of the above.

julia> setassay!(x, "foo", assay(x, 2));
```
