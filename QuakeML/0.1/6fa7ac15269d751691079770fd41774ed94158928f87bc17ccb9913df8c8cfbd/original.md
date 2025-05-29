```
preferred_origin(event; verbose=false) -> origin
```

Return the preferred origin for an `event`.  This may be defined if there is more than one origin given for an event, and the `preferred_origin_id` field is set.  If there is only one origin for this `event`, then that is returned.  If there is no origin associated with this event which matches the stated `preferred_origin_id`, then the first origin is returned and a warning is given when `verbose=true`
