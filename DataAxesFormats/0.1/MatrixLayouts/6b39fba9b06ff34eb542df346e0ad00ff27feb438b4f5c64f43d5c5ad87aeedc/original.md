```
inefficient_action_handler(handler::AbnormalHandler)::AbnormalHandler
```

Specify the [`AbnormalHandler`](@ref) to use when accessing a matrix in an inefficient way ("against the grain"). Returns the previous handler. The default handler is `WarnHandler`.
