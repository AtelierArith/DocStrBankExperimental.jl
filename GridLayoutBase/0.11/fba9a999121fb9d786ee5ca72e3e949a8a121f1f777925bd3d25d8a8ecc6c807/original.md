```
content(g::Union{GridPosition,GridSubposition})
```

Return the one object placed in the `GridLayout` at the `Span` and `Side` stored in the `GridPosition` `g`. If there is more than one object at that position, throw an error.

See also `contents`.
