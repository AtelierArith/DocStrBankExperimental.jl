```
@unnest_wider(df, columns, names_sep)
```

Unnest specified columns of arrays or dictionaries into wider format dataframe with individual columns.

# Arguments

  * `df`: A DataFrame.
  * `columns`: Columns to be unnested. These columns should contain arrays, dictionaries, dataframes, or tuples. Dictionarys headings will be converted to column names.
  * `names_sep`: An optional string to specify the separator for creating new column names. If not provided, defaults to no separator.

# Examples

```jldoctest
julia> df = DataFrame(name = ["Zaki", "Farida"], attributes = [
               Dict("age" => 25, "city" => "New York"),
               Dict("age" => 30, "city" => "Los Angeles")]);

julia> @unnest_wider(df, attributes)
2×3 DataFrame
 Row │ name    city         age   
     │ String  String       Int64 
─────┼────────────────────────────
   1 │ Zaki    New York        25
   2 │ Farida  Los Angeles     30

julia> df2 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c      
     │ Int64  Array…  Array… 
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> @unnest_wider(df2, b:c, names_sep = "_")
2×5 DataFrame
 Row │ a      b_1    b_2    c_1    c_2   
     │ Int64  Int64  Int64  Int64  Int64 
─────┼───────────────────────────────────
   1 │     1      1      2      5      6
   2 │     2      3      4      7      8
```
