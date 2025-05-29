```
contents(gp::GridPosition; exact::Bool = false)
```

Retrieve all objects placed in the `GridLayout` at the `Span` and `Side` stored in the `GridPosition` `gp`. If `exact == true`, elements are only included if they match the `Span` exactly, otherwise they can also be contained within the spanned layout area.
