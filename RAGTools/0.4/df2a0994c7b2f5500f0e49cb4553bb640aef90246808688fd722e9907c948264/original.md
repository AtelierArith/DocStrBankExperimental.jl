```
annotate_support(annotater::TrigramAnnotater, answer::AbstractString,
	context::AbstractVector; min_score::Float64 = 0.5,
	skip_trigrams::Bool = true, hashed::Bool = true,
	sources::Union{Nothing, AbstractVector{<:AbstractString}} = nothing,
	min_source_score::Float64 = 0.25,
	add_sources::Bool = true,
	add_scores::Bool = true, kwargs...)
```

Annotates the `answer` with the overlap/what's supported in `context` and returns the annotated tree of nodes representing the `answer`

Returns a "root" node with children nodes representing the sentences/code blocks in the `answer`. Only the "leaf" nodes are to be printed (to avoid duplication), "leaf" nodes are those with NO children.

Default logic: 

  * Split into sentences/code blocks, then into tokens (~words).
  * Then match each token (~word) exactly.
  * If no exact match found, count trigram-based match (include the surrounding tokens for better contextual awareness).
  * If the match is higher than `min_score`, it's recorded in the `score` of the node.

# Arguments

  * `annotater::TrigramAnnotater`: Annotater to use
  * `answer::AbstractString`: Text to annotate
  * `context::AbstractVector`: Context to annotate against, ie, look for "support" in the texts in `context`
  * `min_score::Float64`: Minimum score to consider a match. Default: 0.5, which means that half of the trigrams of each word should match
  * `skip_trigrams::Bool`: Whether to potentially skip trigram matching if exact full match is found. Default: true
  * `hashed::Bool`: Whether to use hashed trigrams. It's harder to debug, but it's much faster for larger texts (hashed text are held in a Set to deduplicate). Default: true
  * `sources::Union{Nothing, AbstractVector{<:AbstractString}}`: Sources to add at the end of the context. Default: nothing
  * `min_source_score::Float64`: Minimum score to consider/to display a source. Default: 0.25, which means that at least a quarter of the trigrams of each word should match to some context. The threshold is lower than `min_score`, because it's average across ALL words in a block, so it's much harder to match fully with generated text.
  * `add_sources::Bool`: Whether to add sources at the end of each code block/sentence. Sources are addded in the square brackets like "[1]". Default: true
  * `add_scores::Bool`: Whether to add source-matching scores at the end of each code block/sentence. Scores are added in the square brackets like "[0.75]". Default: true
  * kwargs: Additional keyword arguments to pass to `trigram_support!` and `set_node_style!`. See their documentation for more details (eg, customize the colors of the nodes based on the score)

# Example

```julia
annotater = TrigramAnnotater()
context = [
	"This is a test context.", "Another context sentence.", "Final piece of context."]
answer = "This is a test context. Another context sentence."

annotated_root = annotate_support(annotater, answer, context)
pprint(annotated_root) # pretty print the annotated tree
```
