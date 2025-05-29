```
unsubscribe(client::ShadowClient)
```

Unsubscribes from all shadow document topics.

Arguments:

  * `client (ShadowClient)`: Shadow client to use.

Returns a task which completes when the tasks from each [`unsubscribe`](@ref) call complete. Also returns a collection containing the packet ID from each [`unsubscribe`](@ref) call.
