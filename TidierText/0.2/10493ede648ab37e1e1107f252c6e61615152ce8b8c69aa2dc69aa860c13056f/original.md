```
@unnest_regex(df, output_col, input_col, pattern = "\s+", to_lower = false)
```

Splits the text in `input_col` of `df` based on a regex `pattern`, outputting the result to `output_col`.

# Arguments

  * `df`: The input DataFrame.
  * `output_col`: The name of the output column to store the result.
  * `input_col`: The name of the input column containing text to split.
  * `pattern`: The regex pattern to use for splitting text.
  * `to_lower`: An optional boolean that defaults to false which indicates whether to convert text to lowercase before splitting.
  * `strip_non_alphanum`: Optional boolean that defualts to true, which strips non alphanumeric characters

# Returns

  * A new DataFrame with the text split based on the regex pattern.

# Examples

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick brown fox jumps.",
                      "One column and the one row?"],
                      doc = [1, 2]
            );

julia> @unnest_regex(df, word, text, "the")
3×2 DataFrame
 Row │ doc    word                      
     │ Int64  SubStrin…                 
─────┼──────────────────────────────────
   1 │     1  The quick brown fox jumps
   2 │     2  One column and
   3 │     2  one row

julia> @unnest_regex(df, word, text, "the", to_lower = true, strip_non_alphanum = false)
3×2 DataFrame
 Row │ doc    word                   
     │ Int64  SubStrin…              
─────┼───────────────────────────────
   1 │     1  quick brown fox jumps.
   2 │     2  one column and
   3 │     2  one row?
```
