```
get_tags(tagger::PassthroughTagger, docs::AbstractVector{<:AbstractString};
	tags::AbstractVector{<:AbstractVector{<:AbstractString}},
	kwargs...)
```

Pass `tags` directly as Vector of Vectors of strings (ie, `tags[i]` is the tags for `docs[i]`). It then builds the vocabulary from the tags and returns both the tags in matrix form and the vocabulary.
