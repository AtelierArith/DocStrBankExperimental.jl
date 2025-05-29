```
groupby(df, args...)
```

Group a data frame by columns. An alias for

```
groupby(df, Cols(args...))
```

but with a few convenience features.

## Details

`@groupby` does not perform any transformations or allow the generation of new columns. New column generation must be done before `@groupby` is called.

`@groupby` allows mixing of `Symbol` and `String` inputs, such that `@groupby df :A "B"` is supported.

Arguments are not escaped and DataFramesMeta.jl rules for column selection, such as `$` for escaping, do not apply.

## Examples

```julia-repl
julia> df = DataFrame(A = [1, 1], B = [3, 4], C = [6, 6]);
julia> @groupby df :A;
julia> @groupby df :A :B;
julia> @groupby df [:A, :B];
julia> @groupby df :A [:B, :C];
```
