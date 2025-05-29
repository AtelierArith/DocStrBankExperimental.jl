```
sharers(nodes::LNodes)
```

Returns a `Dict` mapping the neighboring rank with the global ids of the nodes shared between it and the local rank.

Note, this `Dict` does not include an entry for the local rank.
