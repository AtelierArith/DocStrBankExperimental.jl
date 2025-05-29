```
create_index(
    fields;
    client=get_search_client(),
    no_term_offsets=false,
    no_field_flags=false,
    stopwords=nothing,
    definition=nothing,
    max_text_fields=false,
    temporary=nothing,
    no_highlight=false,
    no_term_frequencies=false,
    skip_initial_scan=false,
)
create_index(field::AbstractField; kwargs...) = create_index([field]; kwargs...)
```

Creates an index with the given spec. If an index already exists, this will error.

# Arguments

  * `fields`: List of Field objects

# Keywords

  * `client`: Search client
  * `no_term_offsets`: Bool for offsets.
  * `no_field_flags`: Bool for field flags
  * `stopwords`: List of stopwords. If nothing, default stopwords are used.
  * `definition`: Index Definition object.
  * `max_text_fields`: Forces RediSearch to encode indexes as if there were more than 32

text attributes.

  * `temporary`: Create a lightweight temporary index which will expire after the specified

period of inactivity.

  * `no_highlight`: Conserves storage space and memory by disabling highlighting support.
  * `no_term_frequencies`: If true, we avoid saving the term frequencies in the index.
  * `skip_initial_scan`: If true, we do not scan and index.
