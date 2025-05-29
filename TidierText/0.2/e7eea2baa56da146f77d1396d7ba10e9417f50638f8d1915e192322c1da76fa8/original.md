```
get_stopwords()
```

Returns a DataFrame containing English stopwords.

The stopwords come from the `Languages.jl` package: https://github.com/JuliaText/Languages.jl/blob/master/data/stopwords/English.txt.

# Returns

  * `DataFrame` with a single column `word`, each row containing a stopword.

# Examples

```jldoctest
julia> first(get_stopwords(), 5)
5×1 DataFrame
 Row │ word   
     │ String 
─────┼────────
   1 │ a
   2 │ about
   3 │ above
   4 │ across
   5 │ after
```
