```
get_mutations(client::Client)
```

Returns all mutations available from GraphQL server. If introspection has not been performed, will run `full_introspection!(client)`.
