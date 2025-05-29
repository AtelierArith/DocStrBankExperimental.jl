```
Client(index_name::AbstractString; kwargs....) -> Jedis.Client
```

Set the RediSearch Client. Clients contain an index name and a Jedis Client Struct.  Kwargs are included as any Jedis client kwargs

# Fields

  * `index_name::String`: Index name that will be created with the client.
  * `client::Jedis.Client`: Client object made through the Jedis package.

# Examples

```julia-repl
julia> client = Client("myIdx");

julia> client = Client("myIdx"; host="localhost", port=6379);
```
