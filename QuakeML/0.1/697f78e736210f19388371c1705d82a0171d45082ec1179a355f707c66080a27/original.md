```
preferred_focal_mechanism(event; verbose=false) -> focal_mechanism
```

Return the preferred focal mechanism for an `event`.  This may be defined if there is more than one focal mechanism given for an event, and the `preferred_focal_mechanism_id` field is set.  If there is only one focal mechanism for this `event`, then that is returned.  If there is no focal mechanism associated with this event which matches the stated `preferred_focal_mechanism_id`, then the first focal mechanism is returned, and a warning given is `verbose` is `true`.
