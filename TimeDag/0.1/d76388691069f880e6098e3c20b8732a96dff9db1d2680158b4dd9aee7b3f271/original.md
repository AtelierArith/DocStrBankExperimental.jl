```
iterdates(time_of_day::Time=Time(0), tz::TimeZone=tz"UTC", occurrence=1)
```

Create a node which ticks exactly once a day at `time_of_day` in timezone `tz`.

This defaults to midnight in UTC. If `tz` is set otherwise, then each knot will appear at `time_of_day` in that timezone.

Note that:     * All knot times in `TimeDag` are considered to be in UTC.     * It is possible to select a `time_of_day` that does not exist for every day. This will         lead to an exception being raised during evaluation.

In a given knot, each value will be of type `DateTime`, and equal the time of the knot.
