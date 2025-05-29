```
nma_words
```

Returns a DataFrame containing 44 English negators, modals, and adverbs

The NMA words come from a list developed by Saif Mohammad: http://saifmohammad.com/WebPages/SCL.html#NMA

# Returns

  * `DataFrame` with a single column `word`, each row containing a stopword.

# Examples

```jldoctest
julia> first(nma_words, 5)
5×2 DataFrame
 Row │ word       modifier 
     │ String     String   
─────┼─────────────────────
   1 │ cannot     negator
   2 │ could not  negator
   3 │ did not    negator
   4 │ does not   negator
   5 │ had no     negator
```
