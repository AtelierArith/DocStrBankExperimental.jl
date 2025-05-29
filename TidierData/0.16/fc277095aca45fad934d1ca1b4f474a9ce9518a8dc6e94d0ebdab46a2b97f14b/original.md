```
@relocate(df, columns, before = nothing, after = nothing)
```

Rearranges the columns of a data frame. This function allows for moving specified columns to a new position within the data frame, either before or after a given target column. The `columns`, `before`, and `after` arguments all accept tidy selection functions. Only one of `before` or `after` should be specified. If neither are specified, the selected columns will be moved to the beginning of the data frame.

# Arguments

  * `df`: The data frame.
  * `columns`: Column or columns to to be moved.
  * `before`: (Optional) Column or columns before which the specified columns will be moved. If not provided or `nothing`, this argument is ignored.
  * `after`: (Optional) Column or columns after which the specified columns will be moved. If not provided or `nothing`, this argument is ignored.

# Examples

```jldoctest
julia> df = DataFrame(A = 1:5, B = 6:10, C = ["A", "b", "C", "D", "E"], D = ['A', 'B','A', 'B','C'],
                      E = 1:5, F = ["A", "b", "C", "D", "E"]);

julia> @relocate(df, where(is_string), before = where(is_integer))
5×6 DataFrame
 Row │ C       F       A      B      E      D    
     │ String  String  Int64  Int64  Int64  Char 
─────┼───────────────────────────────────────────
   1 │ A       A           1      6      1  A
   2 │ b       b           2      7      2  B
   3 │ C       C           3      8      3  A
   4 │ D       D           4      9      4  B
   5 │ E       E           5     10      5  C


julia> @relocate(df, B, C, D, after = E)
5×6 DataFrame
 Row │ A      E      B      C       D     F      
     │ Int64  Int64  Int64  String  Char  String 
─────┼───────────────────────────────────────────
   1 │     1      1      6  A       A     A
   2 │     2      2      7  b       B     b
   3 │     3      3      8  C       A     C
   4 │     4      4      9  D       B     D
   5 │     5      5     10  E       C     E

julia> @relocate(df, B, C, D, after = starts_with("E"))
5×6 DataFrame
 Row │ A      E      B      C       D     F      
     │ Int64  Int64  Int64  String  Char  String 
─────┼───────────────────────────────────────────
   1 │     1      1      6  A       A     A
   2 │     2      2      7  b       B     b
   3 │     3      3      8  C       A     C
   4 │     4      4      9  D       B     D
   5 │     5      5     10  E       C     E

julia> @relocate(df, B:C) # bring columns to the front
5×6 DataFrame
 Row │ B      C       A      D     E      F      
     │ Int64  String  Int64  Char  Int64  String 
─────┼───────────────────────────────────────────
   1 │     6  A           1  A         1  A
   2 │     7  b           2  B         2  b
   3 │     8  C           3  A         3  C
   4 │     9  D           4  B         4  D
   5 │    10  E           5  C         5  E
```
