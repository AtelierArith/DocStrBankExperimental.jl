```
simplify(p::Path, inds::UnitRange=firstindex(p):lastindex(p))
```

At `inds`, segments of a path are turned into a `CompoundSegment` and styles of a path are turned into a `CompoundStyle`. The method returns a `Paths.Node`, `(segment, style)`.

  * Indexing the path becomes more sane when you can combine several path segments into one logical element. A launcher would have several indices in a path unless you could simplify it.
  * You don't need to think hard about boundaries between straights and turns when you want a continuous styling of a very long path.
