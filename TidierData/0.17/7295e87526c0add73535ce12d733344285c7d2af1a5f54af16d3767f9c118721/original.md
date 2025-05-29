```
@glimpse(df, width = 80)
```

Preview a DataFrame (or GroupedDataFrame).

The `@glimpse` macro is used to preview a DataFrame or GroupedDataFrame. Each column is printed on a separate row, along with its data type and first few elements, with the output truncated based on the `width`.

# Arguments

  * `df`: A DataFrame or GroupedDataFrame.
  * `width`: The width of the output, measured in the number of characters. Defaults to 80.

# Examples

```jldoctest
julia> df = DataFrame(
               a = 1:100, 
               b = 1:100, 
               c = repeat(["a"], 100)
               );

julia> @chain df @glimpse
Rows: 100
Columns: 3
.a             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.b             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.c             String         a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a,

julia> @chain df begin
       @group_by(a)
       @glimpse()
       end
Rows: 100
Columns: 3
Groups: a [100]
.a             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.b             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.c             String         a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a,
```
