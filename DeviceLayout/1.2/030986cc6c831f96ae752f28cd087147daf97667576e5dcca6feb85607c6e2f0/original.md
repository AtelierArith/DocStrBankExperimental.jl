```
transformation(c::GeometryStructure, d::GeometryReference)
```

Given a GeometryStructure `c` containing [`GeometryReference`](@ref) `d` in its tree of references, this function returns a `Transformations.ScaledIsometry` object that lets you translate from the coordinate system of `d` to the coordinate system of `c`.

If the *same exact* `GeometryReference` (as in `===`, same address in memory) is included multiple times in the tree of references, then the resulting transform will be based on the first time it is encountered. The tree is traversed one level at a time to find the reference (optimized for shallow references).

Example: You want to translate (2.0,3.0) in the coordinate system of the referenced coordinate system `d` to the coordinate system of `c`:

```
julia> trans = transformation(c,d)

julia> trans(Point(2.0,3.0))
```
