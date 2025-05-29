```
IndexDefinition(;
    prefix=[],
    filter="",
    language_field="",
    language="",
    score_field="",
    score=1.0,
    payload_field="",
    index_type=IndexType.HASH
) -> IndexDefinition
```

IndexDefinition is used to define a index definition for automatic indexing on  Hash or Json update.

# KeyWords

  * `prefix::AbstractArray{AbstractString}`: Tells the index which keys it should index. Each

prefix should finish with a `:`.

  * `filter::AbstractString`: Filter expression with the full RediSearch aggregation

expression language.

  * `language_field::AbstractString`: If set indicates the document attribute that should be

used as the document language.

  * `language::AbstractString`: If set indicates the default language for documents in the

index. Default to English.

  * `score_field::AbstractString`: If set indicates the document attribute that should be used

as the document's rank based on the user's ranking. Ranking must be between 0.0 and 1.0.  If not set the default score is 1

  * `score::Float64`: If set indicates the default score for documents in the index.

Default score is 1.0.

  * `payload_field::AbstractString`: If set indicates the document attribute that should be

used as a binary safe payload string to the document, that can be evaluated at query time by a custom scoring function, or retrieved to the client.

  * `index_type::Number`: Currently supports HASH (default) and JSON.
