Non-blocking poll for events. Must return whether a client event was consumed, even if no `Event` is added to the queue.

```julia
poll_for_events!(queue::WindowAbstractions.EventQueue)

```
