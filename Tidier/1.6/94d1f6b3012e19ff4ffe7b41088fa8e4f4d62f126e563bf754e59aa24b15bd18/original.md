```
@unnest_longer(df, columns, indices_include=false)
```

Unnest arrays in columns from a DataFrame to create a longer DataFrame with one row for each entry of the array.

# Arguments

  * `df`: A DataFrame.
  * `columns`: Columns to unnest. Can be a column symbols or a range of columns if they align for number of values.
  * `indices_include`: Optional. When set to `true`, adds an index column for each unnested column, which logs the position of each array entry.
  * `keep_empty`: Optional. When set to `true`, rows with empty arrays are kept, not skipped, and unnested as missing.

# Examples

```jldoctest
julia> df = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c      
     │ Int64  Array…  Array… 
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> @unnest_longer(df, 2)
4×3 DataFrame
 Row │ a      b      c      
     │ Int64  Int64  Array… 
─────┼──────────────────────
   1 │     1      1  [5, 6]
   2 │     1      2  [5, 6]
   3 │     2      3  [7, 8]
   4 │     2      4  [7, 8]

julia> @unnest_longer(df, b:c, indices_include = true)
4×5 DataFrame
 Row │ a      b      c      b_id   c_id  
     │ Int64  Int64  Int64  Int64  Int64 
─────┼───────────────────────────────────
   1 │     1      1      5      1      1
   2 │     1      2      6      2      2
   3 │     2      3      7      1      1
   4 │     2      4      8      2      2

julia> df2 = DataFrame(x = 1:4, y = [[], [1, 2, 3], [4, 5], Int[]])
4×2 DataFrame
 Row │ x      y            
     │ Int64  Array…       
─────┼─────────────────────
   1 │     1  Any[]
   2 │     2  Any[1, 2, 3]
   3 │     3  Any[4, 5]
   4 │     4  Any[]

julia> @unnest_longer(df2, y, keep_empty = true)
7×2 DataFrame
 Row │ x      y       
     │ Int64  Any     
─────┼────────────────
   1 │     1  missing 
   2 │     2  1
   3 │     2  2
   4 │     2  3
   5 │     3  4
   6 │     3  5
   7 │     4  missing 
```

```
@unnest_longer(sql_query, columns...)
```

Unnests specified columns into longer format. This function takes multiple columns containing arrays or other nested structures and expands them into a longer format, where each element of the arrays becomes a separate row.

# Arguments

  * `sql_query`: The SQL query
  * `columns...`: One or more columns containing arrays or other nested structures to be unnested.

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> DuckDB.query(db, "
            CREATE TABLE nt (
                id INTEGER,
                data ROW(a INTEGER[], b INTEGER[])
                );
            INSERT INTO nt VALUES
                (1, (ARRAY[1,2], ARRAY[3,4])),
                (2, (ARRAY[5,6], ARRAY[7,8,9])),
                (3, (ARRAY[10,11], ARRAY[12,13]));");

julia> @chain dt(db, :nt) begin 
        @unnest_wider data  
        @unnest_longer a b 
        @collect
       end
7×3 DataFrame
 Row │ id     a        b     
     │ Int32  Int32?   Int32 
─────┼───────────────────────
   1 │     1        1      3
   2 │     1        2      4
   3 │     2        5      7
   4 │     2        6      8
   5 │     2  missing      9
   6 │     3       10     12
   7 │     3       11     13

julia> @chain dt(db, :nt) begin 
        @unnest_wider data  
        @unnest_longer a:b 
        @collect
       end
7×3 DataFrame
 Row │ id     a        b     
     │ Int32  Int32?   Int32 
─────┼───────────────────────
   1 │     1        1      3
   2 │     1        2      4
   3 │     2        5      7
   4 │     2        6      8
   5 │     2  missing      9
   6 │     3       10     12
   7 │     3       11     13
```
