```
@rename!(d, args...)
```

In-place modification of column names.

### Arguments

  * `d` : an AbstractDataFrame
  * `args...` : expressions of the form `:new = :old` specifying the change of a column's name

from "old" to "new". The left- and right-hand side of each expression can be passed as symbol arguments, as in `:old_col`, or strings escaped with `$` as in `$"new_col"`. See  **Details** for a description of accepted values.

### Returns

  * `::AbstractDataFrame`

Inputs to `@rename!` can come in two formats: a `begin ... end` block, or as a series of keyword-like arguments. For example, the following are equivalent:

```julia
@rename! df begin
    :new_col = :old_col
end
```

and

```
@rename!(df, :new_col = :old_col)
```

### Details

Both the left- and right-hand side of an expression specifying a column name assignment can be either a `Symbol` or a `String``escaped with`$` For example `:new = ...`, and `$"new" = ...` are both valid ways of assigning a new column name.

This idea can be extended to pass arbitrary right-hand side expressions. For example, the following are equivalent:

```
@rename!(df, :new = :old1)
```

and

```
@rename!(df, :new = old_col1)
```

### Examples

```
julia> df = DataFrame(old_col1 = rand(5), old_col2 = rand(5),old_col3 = rand(5));

julia> @rename!(df, :new1 = :old_col1)
5×3 DataFrame
 Row │ new1       old_col2   old_col3
     │ Float64    Float64    Float64
─────┼────────────────────────────────
   1 │ 0.0176206  0.493592   0.348072
   2 │ 0.861545   0.512254   0.85763
   3 │ 0.263082   0.0267507  0.696494
   4 │ 0.643179   0.299391   0.780125
   5 │ 0.731267   0.18905    0.767292

julia> df = DataFrame(old_col1 = rand(5), old_col2 = rand(5),old_col3 = rand(5));

julia> @rename!(df, :new1 = :old_col1, :new2 = $"old_col2")
5×3 DataFrame
 Row │ new1       new2       old_col3
     │ Float64    Float64    Float64
─────┼────────────────────────────────
   1 │ 0.0176206  0.493592   0.348072
   2 │ 0.861545   0.512254   0.85763
   3 │ 0.263082   0.0267507  0.696494
   4 │ 0.643179   0.299391   0.780125
   5 │ 0.731267   0.18905    0.767292

julia> df = DataFrame(old_col1 = rand(5), old_col2 = rand(5),old_col3 = rand(5));

julia> @rename!(df, :new1 = $("old_col" * "1"), :new2 = :old_col2)
5×3 DataFrame
 Row │ new1       new2       old_col3
     │ Float64    Float64    Float64
─────┼────────────────────────────────
   1 │ 0.0176206  0.493592   0.348072
   2 │ 0.861545   0.512254   0.85763
   3 │ 0.263082   0.0267507  0.696494
   4 │ 0.643179   0.299391   0.780125
   5 │ 0.731267   0.18905    0.767292
```
