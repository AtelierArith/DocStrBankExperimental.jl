```
@slice(df, exprs...)
```

Select, remove or duplicate rows by indexing their integer positions.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: integer row values. Use positive values to keep the rows, or negative values to drop. Values provided must be either all positive or all negative, and they must be within the range of DataFrames' row numbers.

# Examples

```jldoctest
julia> df = DataFrame(a = repeat('a':'c', inner = 3), b = 1:9, c = 11:19);

julia> @chain df @slice(1:5)
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ a         3     13
   4 │ b         4     14
   5 │ b         5     15

julia> @chain df @slice(-(1:2))
7×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         3     13
   2 │ b         4     14
   3 │ b         5     15
   4 │ b         6     16
   5 │ c         7     17
   6 │ c         8     18
   7 │ c         9     19

julia> @chain df begin
         @group_by(a)
         @slice(1)
         @ungroup
       end
3×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         4     14
   3 │ c         7     17

julia> @chain df begin
         @group_by(a)
         @slice(n())
         @ungroup
       end
3×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         3     13
   2 │ b         6     16
   3 │ c         9     19

julia> @chain df begin
         @group_by(a)
         @slice(-n())
         @ungroup
       end
6×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         4     14
   4 │ b         5     15
   5 │ c         7     17
   6 │ c         8     18

julia> @chain df begin
         @group_by(a)
         @slice(-(2:n()))
         @ungroup
       end
3×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         4     14
   3 │ c         7     17
```
