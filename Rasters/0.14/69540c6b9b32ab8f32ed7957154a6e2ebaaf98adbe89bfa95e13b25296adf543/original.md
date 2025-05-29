```
disaggregate!(dst::AbstractRaster, src::AbstractRaster, scale)
```

Disaggregate array `src` to array `dst` by some scale.

  * `scale`: the aggregation factor, which can be an `Int`, a `Tuple` of `Int` for each dimension, or a `:` colon to mean the whole dimension.  You can also use any `Dimension`, `Selector` or `Int` combination you can usually use in `getindex`. `Tuple` of `Pair` or `NamedTuple` where keys are dimension names will also work. Using a `Selector` will determine the scale by the distance from the start  of the index. Selectors will find the first offset and repeat the same aggregation size for the rest.
