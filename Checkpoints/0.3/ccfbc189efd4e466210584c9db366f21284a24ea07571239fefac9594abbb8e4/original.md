```
checkpoint([prefix], name, data)
checkpoint([prefix], name, data::Pair...)
checkpoint([prefix], name, data::Dict)
```

Defines a data checkpoint with a specified `label` and values `data`. By default checkpoints are no-ops and need to be explicitly configured.

```
checkpoint(session, data)
checkpoint(handler, name, data::Dict)
```

Alternatively, you can also checkpoint with to a session which stages the data to be commited later by `commit!(session)`. Explicitly calling checkpoint on a handler is generally not advised, but is an option.
