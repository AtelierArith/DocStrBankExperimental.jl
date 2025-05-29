```
fill_forward_value(ts::EventSeries, time)
```

Returns the prior (with respect to `time`) `value` in the input `EventSeries`).

```
fill_forward_value(ts::TaggedEventSeries, time)
```

Returns a named tuple with the prior (with respect to `time`) `values`s for each tag in the input `TaggedEventSeries`.

If `time` is before the first timestamp in `EventSeries` / `TaggedEventSeries`, then `nothing` is returned.
