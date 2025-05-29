```
covariate(src, group_a, [group_b])
```

Create a two-group `covariate` referring to `src`, comparing `group_a` to `group_b`.

`src` is one of:

  * `String` - referring to a column in the DataMatrix `obs`.
  * `DataFrame` - with exactly two columns, the first should contain IDs matching IDs in `obs`, and the second should be the covariate.
  * `Annotations` (experimental) - with ID matching the DataMatrix `obs` and a second column for the covariate.

If `src` is a `String` it will refer to a column in the DataMatrix `obs`. `src` can also be an `Annotations` object, with ID matching the DataMatrix `obs`. `group_a` and `group_b` must be values occuring in the column `src`.

If `group_b` is not given, `group_a` will be compared to all other observations.

See also: [`designmatrix`](@ref)
