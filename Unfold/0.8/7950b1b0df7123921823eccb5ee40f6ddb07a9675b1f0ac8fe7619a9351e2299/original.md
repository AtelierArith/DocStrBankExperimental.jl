```
predicttable(model<:UnfoldModel,events=Unfold.events(model),args...;kwargs...)
```

Shortcut to call efficiently call (pseudocode) `result_to_table(predict(...))`.

Returns a tidy DataFrame with the predicted results. Loops all input to `predict`, but really only makes sense to use if you specify either:

`overlap = false` (the default) or `epoch_to = "eventname"`.
