```
preferred_magnitude(event; verbose=false) -> magnitude
```

Return the preferred magnitude for an `event`.  This may be defined if there is more than one magnitude given for an event, and the `preferred_magnitude_id` field is set.  If there is only one magnitude for this `event`, then that is returned.  If there is no magnitude associated with this event which matches the stated `preferred_magnitude_id`, then the first magnitude is returned, and a warning given is `verbose` is `true`.
