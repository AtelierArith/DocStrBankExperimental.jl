```
replace_missing(x, replacement)
```

Replace `missing` values in `x` with a specified `replacement` value.

# Arguments

  * `x`: The input value which can be of any type. If `x` is `missing`, the function will return `replacement`. Otherwise, it returns `x` unaltered.
  * `replacement`: The value to replace `missing` with in `x`.

# Examples

```jldoctest
julia> df = DataFrame(
              a = [1, missing, 3, 4],
              b = [4, 5, missing, 8]
            );

julia> @chain df begin
         @mutate(a = replace_missing(a, 100),
                 b = replace_missing(b, 35))
       end
4×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      4
   2 │   100      5
   3 │     3     35
   4 │     4      8
```
