```
function isshutdown(process::Supervised)
```

Returns `true` if process has a shutdown command in its inbox.

As a side effect remove messages from process inbox until a `shutdown` request is found.
