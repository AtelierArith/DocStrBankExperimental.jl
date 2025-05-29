```
fill_forward_event(ts::EventSeries, time)
```

Returns the prior (with respect to `time`) `Event` in the input `EventSeries`).

```
fill_forward_event(ts::TaggedEventSeries, time)
```

Returns a named tuple with the prior (with respect to `time`) `Event`s for each tag in the input `TaggedEventSeries`.

If `time` is before the first timestamp in `EventSeries` / `TaggedEventSeries`, then `nothing` is returned.
