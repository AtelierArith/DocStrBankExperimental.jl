```
matches(pattern, [flags])
```

Select all columns matching the `pattern`.

# Arguments

  * `pattern`: A string.
  * `flags`: Optional string containing flags. "i" = Do case-insensitive pattern matching. "m" = Treat string as multiple lines. "s" = Treat string as a single line. "x" = Tells the regular expression parser to ignore most whitespace that is neither backslashed nor within a character class. You

can use this to break up your regular expression into (slightly) more readable parts.

# Examples

```julia
julia> df = DataFrame(a_1 = 1:5, a_2 = 11:15, b_1 = 21:25);

julia> @chain df begin 
         @select(matches("^a"))
       end
5×2 DataFrame
 Row │ a_1    a_2   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df begin 
         @select(matches("1$"))
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

julia> @chain df begin 
         @select(matches("A", "i"))
       end
5×2 DataFrame
 Row │ a_1    a_2   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
```
