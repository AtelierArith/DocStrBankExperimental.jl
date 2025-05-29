```
ParameterMessageBehavior()
```

`ParameterMessageBehavior` simplifies the task of an agent wishing to support parameters via `ParameterReq` and `ParameterRsp` messages. An agent providing parameters can advertise its parameters by providing an implementation for the `params(a)` method (or `params(a, ndx)` method for indexed parameters). The method returns a list of name-symbol pairs. Each entry represents a parameter with the specified name, and dispatched using the specified symbol. Get and set requests for the parameter are dispatched to `get(a, Val(symbol))` and `set(a, Val(symbol), value)` methods (or `get(a, Val(symbol), ndx)` and `set(a, Val(symbol), ndx, value)` for indexed parameters). If the method isn't defined, and an agent struct field with the same name is present, it is used to back the parameter.

Setters should return the value that is set, so that it can be sent back to the requesting agent. If a setter returns `nothing`, the actual value is fetched using the getter and then sent to the requesting agent.

An agent may choose to avoid advertising specific parameters by defining `isunlisted(Val(symbol))` method for the parameter to return `true`. Similarly, an agent may choose to mark a parameter as read-only by defining the `isreadonly(Val(symbol))` method for the parameter to return `true`.

Parameter change events may be captured by defining a `onparamchange(a::Agent, b::Behavior, param, ndx, value)` method for the parameter.

The default `init()` for an agent automatically adds a `ParameterMessageBehavior` to dispatch handle parameters for an agent, and so an agent can benefit from this behavior without explicitly adding it. If an agent provides its own `init()` method and wishes to support parameters, it should add this behavior during `init()`.

# Examples:

```julia
using Fjage

@agent struct MyAgent
  param1::Int = 1
  param2::Float64 = 0.0
  secret::String = "top secret message"
  x::Int = 2
end

Fjage.param(a::MyAgent) = [
  "MyAgent.param1" => :param1,    # backed by a.param1
  "MyAgent.param2" => :param2,    # backed by a.param2, but readonly
  "MyAgent.X" => :X,              # backed by getter and setter
  "MyAgent.Y" => :Y,              # backed by getter only, so readonly
  "MyAgent.secret" => :secret     # backed by a.secret, but unlisted
]

Fjage.isreadonly(a::MyAgent, ::Val{:param2}) = true
Fjage.isunlisted(a::MyAgent, ::Val{:secret}) = true

Fjage.get(a::MyAgent, ::Val{:X}) = a.x
Fjage.set(a::MyAgent, ::Val{:X}, value) = (a.x = clamp(value, 0, 10))
Fjage.get(a::MyAgent, ::Val{:Y}) = a.x + 27
```
