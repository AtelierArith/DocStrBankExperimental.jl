`@curry exprs...`

Injects `exprs` as the first arguments in every first-level method calls of the last argument. Like [`curry`](@ref), but does not generate an anonymous method instance that can be passed to other methods.

# Example

```julia
logid = 42
@curry "Log " logid ": " begin
   println(420)
   println(69)
end
# prints "Log 42: 420"
# prints "Log 42: 69"
```
