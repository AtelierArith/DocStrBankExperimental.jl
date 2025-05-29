```
setsegment!(n::Node, s::Segment)
```

Set the segment associated with node `n` to `s`. If `reconcile`, then modify fields as appropriate for internal consistency (possibly including other linked nodes).
