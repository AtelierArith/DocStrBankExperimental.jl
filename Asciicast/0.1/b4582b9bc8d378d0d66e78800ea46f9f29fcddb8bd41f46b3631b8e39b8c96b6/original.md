```
write_event!(cast::Cast, event_type::EventType, event_data::AbstractString)
write_event!(cast::Cast, event::Event)
```

Write an event to `cast` of type `event_type` (either `OutputEvent` or `InputEvent`) with data given by `event_data`.
