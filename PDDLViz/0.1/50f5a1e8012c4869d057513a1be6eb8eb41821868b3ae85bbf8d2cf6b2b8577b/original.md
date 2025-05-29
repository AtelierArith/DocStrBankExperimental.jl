```
add_controller!(canvas, controller, domain, [init_state];
                show_controls::Bool=false)
```

Adds a `controller` to a `canvas` for a given PDDL `domain`. An initial state `init_state` can be specified to enable restart functionality.
