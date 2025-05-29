```
gn_url()
```

Return the default GeneNetwork server API URL.

All user-level functions optionally take a GeneNetwork server URL that could be different from the standard URL in case one wanted to query a different instance of the server.

# Example

```jldoctest
julia> gn_url()
"https://genenetwork.org/api/v_pre1/"
```
