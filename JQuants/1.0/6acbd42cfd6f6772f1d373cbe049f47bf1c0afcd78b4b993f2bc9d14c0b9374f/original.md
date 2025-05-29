```
fetch(api::API, kwargs...)
```

Fetch data from JQuants API.

# Arguments

  * `api::API`: API struct to fetch data from
  * `json::Bool`: If true, return a vector of the raw JSON strings. The number of elements in the vector is equal to the number of pages of the API response. If false, return a DataFrame. Default is false.

# Examples

```julia
julia> fetch(ListedInfo(code="72030"));

julia> fetch(ListedInfo(code="72030"), json=true);
```
