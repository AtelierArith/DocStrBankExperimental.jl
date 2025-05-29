```
get_keywords(
	processor::KeywordsProcessor, docs::AbstractVector{<:AbstractString};
	verbose::Bool = true,
	stemmer = nothing,
	stopwords::Set{String} = Set(STOPWORDS),
	return_keywords::Bool = false,
	min_length::Integer = 3,
	min_term_freq::Int = 1, max_terms::Int = typemax(Int),
	kwargs...)
```

Generate a `DocumentTermMatrix` from a vector of `docs` using the provided `stemmer` and `stopwords`.

# Arguments

  * `docs`: A vector of strings to be embedded.
  * `verbose`: A boolean flag for verbose output. Default is `true`.
  * `stemmer`: A stemmer to use for stemming. Default is `nothing`.
  * `stopwords`: A set of stopwords to remove. Default is `Set(STOPWORDS)`.
  * `return_keywords`: A boolean flag for returning the keywords. Default is `false`. Useful for query processing in search time.
  * `min_length`: The minimum length of the keywords. Default is `3`.
  * `min_term_freq`: The minimum frequency a term must have to be included in the vocabulary, eg, `min_term_freq = 2` means only terms that appear at least twice will be included.
  * `max_terms`: The maximum number of terms to include in the vocabulary, eg, `max_terms = 100` means only the 100 most frequent terms will be included.
