```
@unnest_characters(df, output_col, input_col, to_lower = false, strip_non_alphanum = true)
```

Splits the text in `input_col` of `df` into separate characters, outputting the result to `output_col`.

# Arguments

  * `df`: The input DataFrame.
  * `output_col`: The name of the output column to store the characters.
  * `input_col`: The name of the input column containing text.
  * `to_lower`: An optional boolean that defaults to false which indicates whether to convert text to lowercase before splitting.
  * `strip_non_alphanum`: Optional boolean that defualts to true, which strips non alphanumeric characters

# Returns

  * A new DataFrame with the text split into characters.

# Examples

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick.", "Nice."],
              doc = [1, 2]);

julia> @unnest_characters(df, term, text, to_lower = false, strip_non_alphanum = false)
15×2 DataFrame
 Row │ doc    term 
     │ Int64  Char 
─────┼─────────────
   1 │     1  T
   2 │     1  h
   3 │     1  e
   4 │     1
   5 │     1  q
   6 │     1  u
   7 │     1  i
   8 │     1  c
   9 │     1  k
  10 │     1  .
  11 │     2  N
  12 │     2  i
  13 │     2  c
  14 │     2  e
  15 │     2  .

julia> @unnest_characters(df, term, text, to_lower = true)
13×2 DataFrame
 Row │ doc    term 
     │ Int64  Char 
─────┼─────────────
   1 │     1  t
   2 │     1  h
   3 │     1  e
   4 │     1
   5 │     1  q
   6 │     1  u
   7 │     1  i
   8 │     1  c
   9 │     1  k
  10 │     2  n
  11 │     2  i
  12 │     2  c
  13 │     2  e
```
