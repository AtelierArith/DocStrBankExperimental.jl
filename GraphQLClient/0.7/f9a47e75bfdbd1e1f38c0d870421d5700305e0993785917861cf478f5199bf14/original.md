```
get_subscriptions(client::Client)
```

Returns all subscriptions available from GraphQL server. If introspection has not been performed, will run `full_introspection!(client)`.
