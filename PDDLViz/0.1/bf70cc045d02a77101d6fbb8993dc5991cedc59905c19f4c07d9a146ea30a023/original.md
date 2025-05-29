```
ControlRecorder(record_actions = true, record_states = false)
```

Callback function for a [`Controller`](@ref) that records actions and states. After constructing a `recorder`, the recorded values can be accessed via `recorder.actions` and `recorder.states`.
