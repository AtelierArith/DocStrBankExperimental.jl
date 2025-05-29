```
lowerleft(ent::AbstractGeometry)
lowerleft(ents)
```

Return the lower-left-most corner of a rectangle bounding `ent` or `ents`. Note that this point doesn't have to be in `ent`.

For iterable `ents`, entities with bounding rectanges of zero width and height will be excluded.
