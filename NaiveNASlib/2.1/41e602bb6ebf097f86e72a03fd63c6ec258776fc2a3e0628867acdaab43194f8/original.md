```
remove_edge!(from::AbstractVertex, to::AbstractVertex; [nr], [strategy])
```

Remove edge from `from` to `to`.

If there are multiple edges from `from` to `to` then `nr` can be used to distinguish which one shall be removed.

Sizes will be adjusted based on given `strategy`.
