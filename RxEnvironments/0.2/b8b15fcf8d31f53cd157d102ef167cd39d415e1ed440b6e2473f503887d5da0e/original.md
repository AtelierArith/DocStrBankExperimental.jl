```
receive!(recipient::AbstractEntity, emitter::AbstractEntity, observation::Any)
```

Receive an observation from `emitter` and update the state of `recipient` accordingly.

See also: [`RxEnvironments.send!`](@ref)
