This module extends the idea behind `Base.Fix1` and `Base.Fix2` to any function and a simple indexing syntax, similar to array indexing, to create delayed evaluation function objects. This package relies on type piracy, defining `Base.getindex` for `Base.Callable`.

Examples:

```
`sin[1.0]() == sin(1.0)`

`map[!,[1,2,3]](x->x+1) == map(x->x+1,[1,2,3])`

`map[!][[1,2,3]]() == map(x->x+1,[1,2,3])`

`sort[by=x->x[1]]([(2,:a),(1,:b)]) == sort([(2,:a),(1,:b)];by=x->x[1])`
```
