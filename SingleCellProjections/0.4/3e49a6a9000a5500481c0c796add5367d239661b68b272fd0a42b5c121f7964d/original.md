```
covariate(src, type=:auto)
```

Create a `covariate` referring to `src`.

`src` is one of:

  * `String` - referring to a column in the DataMatrix `obs`.
  * `DataFrame` - with exactly two columns, the first should contain IDs matching IDs in `obs`, and the second should be the covariate.
  * `Annotations` (experimental) - with ID matching the DataMatrix `obs` and a second column for the covariate.

`type` must be one of `:auto`, `:numerical`, `:categorical`, `:twogroup` and `:intercept`. `:auto` means auto-detection by checking if the values in the column are numerical or categorical. `type==:intercept` adds an intercept to the model (in which case the `src` parameter is ignored).

See also: [`designmatrix`](@ref)
