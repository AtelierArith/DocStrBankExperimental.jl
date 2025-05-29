```
MessageBehavior(action, millis)
MessageBehavior(action, filt, millis)
```

Create a behavior that runs every time a message arrives. The `action(a::Agent, b::Behavior, msg)` function is called when a message arrives. The `onstart` and `onend` fields in the behavior may be set to functions that are called when the behavior is initialized and terminates. Both functions are called with similar parameters as `action`.

If a filter `filt` is specified, only messages matching the filter trigger this behavior. A filter may be a message class or a function that takes the message as an argument and returns `true` to accept, `false` to reject.

If multiple `MessageBehavior` that match a message are active, only one of them will receive the message. The behavior to receive is the message is chosen based on its `priority` field. Messages with filters are given higher default priority than ones without filters.

The default `init()` for an agent automatically adds a `MessageBehavior` to dispatch messages to a `processrequest()` or `processmessage()` method. An agent may therefore process messages by providing methods for those functions. However, if an agent provides its own `init()` method, it should use `MessageBehavior` to handle incoming messages.

# Examples:

```julia
using Fjage

const MySpecialNtf = MessageClass(@__MODULE__, "MySpecialNtf")

@agent struct MyAgent end

function Fjage.init(a::MyAgent)
  add(a, MessageBehavior(MySpecialNtf) do a, b, msg
    @info "Got a special message: $msg"
  end)
  add(a, MessageBehavior() do a, b, msg
    @info "Got a not-so-special message: $msg"
  end)
end
```
