```
ends_with(suffix)
```

Select all columns ending with the `suffix`.

# Arguments

  * `suffix`: A string.

# Examples

```julia
julia> df = DataFrame(a_1 = 1:5, a_2 = 11:15, b_1 = 21:25);

julia> @chain df begin 
         @select(ends_with("1"))
       end
5×2 DataFrame
 Row │ a_1    b_1   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     21
   2 │     2     22
   3 │     3     23
   4 │     4     24
   5 │     5     25
```
