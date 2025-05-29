```
ActorCritic(;actor, critic, optimizer=Adam())
```

The `actor` part must return logits (*Do not use softmax in the last layer!*), and the `critic` part must return a state value.
