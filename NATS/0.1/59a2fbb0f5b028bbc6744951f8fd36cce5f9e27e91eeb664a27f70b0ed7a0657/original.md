```julia
unsubscribe(connection, sub; max_msgs)

```

Unsubscrible from a subject. `sub` is an object returned from `subscribe` or `reply`.

Optional keyword arguments are:

  * `max_msgs`: maximum number of messages server will send after `unsubscribe` message received in server side, what can occur after some time lag
