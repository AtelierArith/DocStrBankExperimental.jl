```
get_chunks(chunker::AbstractChunker,
	files_or_docs::Vector{<:AbstractString};
	sources::AbstractVector{<:AbstractString} = files_or_docs,
	verbose::Bool = true,
	separators = ["\n\n", ". ", "\n", " "], max_length::Int = 256)
```

Chunks the provided `files_or_docs` into chunks of maximum length `max_length` (if possible with provided `separators`).

Supports two modes of operation:

  * `chunker = FileChunker()`: The function opens each file in `files_or_docs` and reads its contents.
  * `chunker = TextChunker()`: The function assumes that `files_or_docs` is a vector of strings to be chunked, you MUST provide corresponding `sources`.

# Arguments

  * `files_or_docs`: A vector of valid file paths OR string documents to be chunked.
  * `separators`: A list of strings used as separators for splitting the text in each file into chunks. Default is `[\n\n", ". ", "\n", " "]`.  See `recursive_splitter` for more details.
  * `max_length`: The maximum length of each chunk (if possible with provided separators). Default is 256.
  * `sources`: A vector of strings indicating the source of each chunk. Default is equal to `files_or_docs` (for `reader=:files`)
