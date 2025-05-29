Search lexicon `lex` for string `s`.

```julia
search(lex, s; searchscope, simplified, case_sensitive)

```

Optional parameters:

  * `searchscope`: one of `SearchScope.LEMMA`, `SearchScope.ARTICLE`, or `SearchScope.ALL`.  Default: `SearchScope.ALL`.
  * `simplified`: a `Lexicon` formatted for searching.  Default: `nothing`.
  * `case_sensitive`: `true` if case should be taken into account in matching.  Default: `true`.
