```
@unnest_ngrams(df, output_col, input_col, n, to_lower = false)
```

Creates n-grams from the text in `input_col` of `df`, outputting the result to `output_col`.

# Arguments

  * `df`: The input DataFrame.
  * `output_col`: The name of the output column to store the n-grams.
  * `input_col`: The name of the input column containing text.
  * `n`: The size of the n-grams.
  * `to_lower`: An optional boolean that defaults to false which indicates whether to convert text to lowercase before splitting.
  * `strip_non_alphanum`: Optional boolean that defualts to true, which strips non alphanumeric characters

# Returns

  * A new DataFrame with the n-grams.

# Examples

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick brown fox jumps.",
                      "The sun rises in the east."],
                      doc = [1, 2]
            );

julia> @unnest_ngrams(df, term, text, 2, to_lower = false)
9×2 DataFrame
 Row │ doc    term        
     │ Int64  String      
─────┼────────────────────
   1 │     1  The quick
   2 │     1  quick brown
   3 │     1  brown fox
   4 │     1  fox jumps
   5 │     2  The sun
   6 │     2  sun rises
   7 │     2  rises in
   8 │     2  in the
   9 │     2  the east

julia> @unnest_ngrams(df, term, text, 2)
9×2 DataFrame
 Row │ doc    term        
     │ Int64  String      
─────┼────────────────────
   1 │     1  The quick
   2 │     1  quick brown
   3 │     1  brown fox
   4 │     1  fox jumps
   5 │     2  The sun
   6 │     2  sun rises
   7 │     2  rises in
   8 │     2  in the
   9 │     2  the east   
```
