```
timespan_start(ctx, category::Symbol, id, tl)
```

Generates an `Event{:start}` which denotes the start of an event. The event is categorized by `category`, and uniquely identified by `id`; these two must be the same passed to `timespan_finish` to close the event. `tl` is the "timeline" of the event, which is just an arbitrary payload attached to the event.
