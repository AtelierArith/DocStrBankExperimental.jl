```
Query(
    query_string::AbstractString;
    offset = 0,
    num = 10,
    no_content = false,
    no_stopwords = false,
    fields = [],
    verbatim = false,
    with_payloads = false,
    with_scores = false,
    scorer = nothing,
    filters = [],
    ids = [],
    slop = -1,
    in_order = false,
    sortby = nothing,
    return_fields = [],
    summarize_fields = [],
    highlight_fields = [],
    language = nothing
)::Query
```

Creates a query instance that can be used to search a RediSearch instance

# Arguments

  * `query_string::String`

# KeyWords

  * `offset::Integer`
  * `num::Integer`
  * `no_content::Bool`
  * `no_stopwords::Bool`
  * `fields::AbstractArray`
  * `verbatim::Bool`verbatim setting for
  * `with_payloads::Bool`
  * `with_scores::Bool`
  * `scorer::Union{String, Nothing}`
  * `filters::AbstractArray{AbstractFilter}`
  * `ids::AbstractArray`
  * `slop::Integer`
  * `in_order::Bool`
  * `sortby::Union{AbstractFilter, Nothing}`
  * `return_fields::AbstractArray`
  * `summarize_fields::AbstractArray`
  * `highlight_fields::AbstractArray`
  * `language::Union{String, Nothing}`

# Returns

  * `Query::AbstractQuery`
