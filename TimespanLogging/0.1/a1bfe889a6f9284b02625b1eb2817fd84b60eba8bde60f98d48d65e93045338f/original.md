```
timespan_finish(ctx, category::Symbol, id, tl)
```

Generates an `Event{:finish}` which denotes the end of an event. The event is categorized by `category`, and uniquely identified by `id`; these two must be the same as previously passed to `timespan_start`. `tl` is the "timeline" of the event, which is just an arbitrary payload attached to the event.
