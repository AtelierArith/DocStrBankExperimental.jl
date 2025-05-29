```
missing_if(x, value)
```

Replace a specific `value` with `missing` in `x`.

## Arguments

  * `x`: The input value which can be of any type. If `x` is already `missing` or equals `value`, the function will return `missing`. Otherwise, it returns `x` unaltered.
  * `value`: The specific value to be checked against.

## Examples

```jldoctest
julia> df = DataFrame(
              a = [1, missing, 3, 4],
              b = ["apple", "apple", "banana", "cherry"]
            );

julia> @chain df begin
         @mutate(a = missing_if(a, 4), 
                 b = missing_if(b, "apple"))
       end
4×2 DataFrame
 Row │ a        b       
     │ Int64?   String? 
─────┼──────────────────
   1 │       1  missing 
   2 │ missing  missing 
   3 │       3  banana
   4 │ missing  cherry
```
