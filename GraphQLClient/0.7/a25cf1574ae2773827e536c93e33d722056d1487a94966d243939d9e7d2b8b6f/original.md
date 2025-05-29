```
Alias
```

Contains an alias for a GraphQL field or query. `Alias`es can be used in the `output_fields` keyword argument as well as directly instead of query, mutation and subscription names.

# Examples

Using an `Alias` instead of the query name:

```jldoctest alias_label; setup=:(using GraphQLClient)
julia> client = Client("https://countries.trevorblades.com");

julia> alias = Alias("country_alias", "country");

julia> query(client, alias, query_args=Dict("code"=>"BR"), output_fields=["name"]).data
Dict{String, Any} with 1 entry:
  "country_alias" => Dict{String, Any}("name"=>"Brazil")

```

Using an `Alias` in `output_fields`:

```jldoctest alias_label; setup=:(using GraphQLClient)
julia> field_alias = Alias("country_name_alias", "name");

julia> query(client, "country", query_args=Dict("code"=>"BR"), output_fields=[field_alias]).data
Dict{String, Any} with 1 entry:
  "country" => Dict{String, Any}("country_name_alias"=>"Brazil")
```
