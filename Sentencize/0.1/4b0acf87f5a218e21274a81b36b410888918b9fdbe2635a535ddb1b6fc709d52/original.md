```
split_sentence(text::AbstractString; prefixes::Dict{<:AbstractString,PrefixType}=Dict{String,PrefixType}(), prefix_file::Union{String,Nothing}=nothing, lang::Union{String,Nothing}="en")
```

Splits a `text` into sentences.

# Arguments

  * `text::AbstractString`: The text to split into sentences.
  * `prefixes::Dict{<:AbstractString,PrefixType}`: Optional. A dictionary of non-breaking prefixes.
  * `prefix_file::Union{String,Nothing}`: Optional. A path to a file containing non-breaking prefixes to add to provided `prefixes`.
  * `lang::Union{String,Nothing}`: Optional. The language of the non-breaking prefixes (see `?SUPPORTED_LANG` for available languages) to be added to `prefixes` Default is "en" (=English).

# Examples

```julia
split_sentence("This is a paragraph. It contains several sentences. "But why," you ask?")
# Output: ["This is a paragraph.", "It contains several sentences.", ""But why," you ask?"]
```
