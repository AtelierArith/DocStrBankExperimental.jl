```
carpet(n; kind=:circular)
```

Draw a circular carpet centered at the origin, using current Luxor parameters.

If `kind` is not `:circular`, the carpet will be a square.

Points that can't be rendered are not included in the final shape.
