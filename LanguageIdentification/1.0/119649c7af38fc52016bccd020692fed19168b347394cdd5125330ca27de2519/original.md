```
langprob(text, languages::Vector{String}, profiles::Vector{Dict{Vector{UInt8}, Float32}}; topk=5, ngram=NGRAM)
```

Returns the probability distribution of the language of the given text based on the provided language profiles.

# Arguments

  * `text`: A string or a collection of strings to be analyzed for language identification.
  * `languages::Vector{String}`: A list of languages to choose from. If this argument is not provided, all the languages returned by the [`supported_languages`](@ref) function will be used.
  * `profiles::Vector{Dict{Vector{UInt8}, Float32}}`: The language profiles to use for identification. If this argument is not provided, the default profiles will be used.
  * `topk::Int`: The number of candidates to return. The default value is 5.
  * `ngram::Union{Int, AbstractVector}`: The length of utf-8 byte n-grams to use for language detection. The default value is the value set in [`initialize`](@ref), and should not exceed that value.

# Returns

  * A list of the `topk` languages and their probabilities.
