```
langid(text, languages::Vector{String}, profiles::Vector{Dict{Vector{UInt8}, Float32}}; ngram=NGRAM)
```

Return the language of the given text based on the provided language profiles.

# Arguments

  * `text`: A string or a collection of strings to be analyzed for language identification.
  * `languages::Vector{String}`: The list of languages to choose from. Omitting this argument will use all supported languages.
  * `profiles::Vector{Dict{Vector{UInt8}, Float32}}`: The language profiles to use for identification. Omitting this argument will use the default profiles.
  * `ngram::Union{Int, AbstractVector}`: The length of utf-8 byte n-grams to use for language detection. The default value is the value set in [`initialize`](@ref), and should not exceed that value.

# Returns

  * The language of the given text.
