```
abstract type Tokenized end
```

Tokenized messages can be tracked automatically by the scheduler.

When an actor sends out a [`Request`](@ref), a timeout will be set up to track the fulfillment of the request. When a `Response` with the same token is received, the timeout will be cancelled. See also: [`send`](@ref).
