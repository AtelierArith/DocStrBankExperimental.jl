```
get_queries(client::Client)
```

Returns all queries available from GraphQL server. If introspection has not been performed, will run `full_introspection!(client)`.
