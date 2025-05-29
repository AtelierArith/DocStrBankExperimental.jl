```
@unnest_tokens(df, output_col, input_col, to_lower = false)
```

Tokenizes the text in `input_col` of `df` into separate words, outputting the result to `output_col`.

# Arguments

  * `df`: The input DataFrame.
  * `output_col`: The name of the output column to store the tokens.
  * `input_col`: The name of the input column containing text to tokenize.
  * `to_lower`: An optional boolean that defaults to false which indicates whether to convert text to lowercase before splitting.
  * `strip_non_alphanum`: Optional boolean that defualts to true, which strips non alphanumeric characters

# Returns

  * A new DataFrame with the tokenized text.

# Examples

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick brown fox jumps.",
                      "One column and the one row?"],
                      doc = [1, 2]
            );

julia> @unnest_tokens(df, word, text, strip_non_alphanum = false)
11×2 DataFrame
 Row │ doc    word      
     │ Int64  SubStrin… 
─────┼──────────────────
   1 │     1  The
   2 │     1  quick
   3 │     1  brown
   4 │     1  fox
   5 │     1  jumps.
   6 │     2  One
   7 │     2  column
   8 │     2  and
   9 │     2  the
  10 │     2  one
  11 │     2  row?

julia> @unnest_tokens(df, word, text, to_lower = true)
11×2 DataFrame
 Row │ doc    word      
     │ Int64  SubStrin… 
─────┼──────────────────
   1 │     1  the
   2 │     1  quick
   3 │     1  brown
   4 │     1  fox
   5 │     1  jumps
   6 │     2  one
   7 │     2  column
   8 │     2  and
   9 │     2  the
  10 │     2  one
  11 │     2  row
```
