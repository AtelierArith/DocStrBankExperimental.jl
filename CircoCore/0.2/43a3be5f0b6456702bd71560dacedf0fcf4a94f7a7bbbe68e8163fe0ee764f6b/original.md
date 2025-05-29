```
Subscribe(eventtype::Type, subscriber::Union{Actor, Addr}, filter::Union{Nothing, String, Function} = nothing)
```

Message for subscribing to events of the given `eventtype`.

The subscription can be optionally filtered by a topic string or a predicate function. Filtering and subscription management will be done by the event dispatcher, which is a separate actor.

`eventtype` must be concrete.

# Examples

```julia
    fs = getname(service, "fs")
    send(service, me, fs, Subscribe(FSEvent, me, "MODIFY"))
    send(service, me, fs, Subscribe(FSEvent, me, event -> event.path == "test.txt"))
```
