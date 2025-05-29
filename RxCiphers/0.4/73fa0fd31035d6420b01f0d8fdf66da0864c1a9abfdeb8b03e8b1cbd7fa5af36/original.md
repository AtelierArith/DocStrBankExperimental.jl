```
Txt
```

A wrapper for strings that handles tokenisation

# Fields

  * `raw` stores the latest string version of the text, is updated on construction and `untokenise`
  * `cases` is a `BitVector` containing the case of each corresponding `Char` in the `raw`, initialised only on construction
  * `charspace` stores the `NCharSpace{N}` of the text
  * `tokenised` stores the token values, is updated under most cipher calls
  * `frozen` stores a `Dict` of `index => string` for substrings that are not tokenised, so they may be reinserted
