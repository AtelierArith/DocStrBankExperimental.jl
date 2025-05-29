```
@rename(d, args...)
```

Change column names.

### Arguments

  * `d` : an AbstractDataFrame
  * `args...` : expressions of the form `:new = :old` specifying the change of a column's name

from "old" to "new". The left- and right-hand side of each expression can be passed as symbol arguments, as in `:old_col`, or strings escaped with `$` as in `$"new_col"`. See  **Details** for a description of accepted values.

### Returns

  * `::AbstractDataFrame`

Inputs to `@rename` can come in two formats: a `begin ... end` block, or as a series of keyword-like arguments. For example, the following are equivalent:

```julia
@rename df begin
    :new_col = :old_col
end
```

and

```
@rename df :new_col = :old_col
@rename(df, :new_col = :old_col)
```

### Details

Both the left- and right-hand side of an expression specifying a column name assignment can be either a `Symbol` or an `AbstractString` (which may contain apces) escaped with `$`. For example `:new = ...`, and `$"new" = ...` are both valid ways of assigning a new column name.

This idea can be extended to pass arbitrary right-hand side expressions. For example, the following are equivalent:

```
@rename(df, :new = :old1)
```

and

```
@rename(df, :new = old_col1)
```

The right-hand side can additionally be an `Integer`, escaped with $, to indicate column position. For example, to rename the 4th column in a data frame to a new name, write `@rename df :newname = $`.

### Examples

```
julia> df = DataFrame(old_col1 = 1:5, old_col2 = 11:15, old_col3 = 21:25);

julia> @rename(df, :new1 = :old_col1)
5×3 DataFrame
 Row │ new1   old_col2  old_col3
     │ Int64  Int64     Int64
─────┼───────────────────────────
   1 │     1        11        21
   2 │     2        12        22
   3 │     3        13        23
   4 │     4        14        24
   5 │     5        15        25

julia> @rename(df, :new1 = :old_col1, :new2 = $"old_col2")
5×3 DataFrame
 Row │ new1   new2   old_col3
     │ Int64  Int64  Int64
─────┼────────────────────────
   1 │     1     11        21
   2 │     2     12        22
   3 │     3     13        23
   4 │     4     14        24
   5 │     5     15        25

julia> @rename(df, :new1 = $("old_col" * "1"), :new2 = :old_col2)
5×3 DataFrame
 Row │ new1   new2   old_col3
     │ Int64  Int64  Int64
─────┼────────────────────────
   1 │     1     11        21
   2 │     2     12        22
   3 │     3     13        23
   4 │     4     14        24
   5 │     5     15        25

julia> @rename df $("New with spaces") = :old_col1
5×3 DataFrame
 Row │ New with spaces  old_col2  old_col3
     │ Int64            Int64     Int64
─────┼─────────────────────────────────────
   1 │               1        11        21
   2 │               2        12        22
   3 │               3        13        23
   4 │               4        14        24
   5 │               5        15        25

julia> @rename df :new_col2 = $2
5×3 DataFrame
 Row │ old_col1  new_col2  old_col3
     │ Int64     Int64     Int64
─────┼──────────────────────────────
   1 │        1        11        21
   2 │        2        12        22
   3 │        3        13        23
   4 │        4        14        24
   5 │        5        15        25
```
