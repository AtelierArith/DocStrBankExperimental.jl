```
separate_rows(df, columns..., sep)
```

Split the contents of specified columns in a DataFrame into multiple rows based on a given delimiter.

# Arguments

  * `df`: A DataFrame
  * `columns`: A column or multiple columns to be split. Can be a mix of integers and column names.
  * `sep`: The string or character or regular expression used to split the column values.

# Examples

```jldoctest
julia> df = DataFrame(a = 1:3,
                      b = ["a", "aa;bb;cc", "dd;ee"],
                      c = ["1", "2;3;4", "5;6"],
                      d = ["7", "8;9;10", "11;12"])
3×4 DataFrame
 Row │ a      b         c       d      
     │ Int64  String    String  String 
─────┼─────────────────────────────────
   1 │     1  a         1       7
   2 │     2  aa;bb;cc  2;3;4   8;9;10
   3 │     3  dd;ee     5;6     11;12

julia> @separate_rows(df, 2, 4, ";")
6×4 DataFrame
 Row │ a      b          c       d         
     │ Int64  SubStrin…  String  SubStrin… 
─────┼─────────────────────────────────────
   1 │     1  a          1       7
   2 │     2  aa         2;3;4   8
   3 │     2  bb         2;3;4   9
   4 │     2  cc         2;3;4   10
   5 │     3  dd         5;6     11
   6 │     3  ee         5;6     12

julia> @separate_rows(df, b:d, ";")
6×4 DataFrame
 Row │ a      b          c          d         
     │ Int64  SubStrin…  SubStrin…  SubStrin… 
─────┼────────────────────────────────────────
   1 │     1  a          1          7
   2 │     2  aa         2          8
   3 │     2  bb         3          9
   4 │     2  cc         4          10
   5 │     3  dd         5          11
   6 │     3  ee         6          12
```
