```
send(service, sender::Actor, to::Addr, messagebody::Any; energy::Real = 1, timeout::Real = 2.0)
```

Send a message from an actor to an another.

Part of the actor API, can be called from a lifecycle callback, providing the `service` you got.

`messagebody` can be of any type, but a current limitation of inter-node communication is that the serialized form of `messagebody` must fit in an IPv4 UDP packet with ~100 bytes margin. The exact value depends on the MTU size of the network and changing implementation details, but 1380 bytes can be considered safe. You may be able to tune your system to get higher values.

If `messagebody` is a `Request`, a timeout will be set for the token of it. The `timeout` keyword argument can be used to control the deadline (seconds).

`energy` sets the energy and sign of the Infoton attached to the message (if the infoton optimizer is running).

# Examples

```julia
const QUERY = "The Ultimate Question of Life, The Universe, and Everything."

mutable struct MyActor <: Actor{TCoreState}
    searcher::Addr
    core::CoreState
    MyActor() = new()
end

struct Start end

struct Search
    query::String
end

[...] # Spawn the searcher or receive its address


function CircoCore.onmessage(me::MyActor, message::Start, service)
    send(service,
            me,
            me.searcher,
            Search(QUERY, addr(me)))
end
```

# Implementation

Please note that `service` is always the last argument of lifecycle callbacks like `onmessage`. It's because `onmessage` is dynamically dispatched, and `service` provides no information about where to dispatch. (Only one service instance exists as of `v"0.2.0"`) Listing it at the end improves performance.

On the other hand, actor API endpoints like `send` are always statically dispatched, thus they can accept the service as their first argument, allowing the user to treat e.g. "`spawn(service`" as a single unit of thought and not forget to write out the ballast `service`.

Consistency is just as important as convenience. But performance is king.
