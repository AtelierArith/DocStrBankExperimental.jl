`DelayEval{F,T}(f,x,kw)` returns an object for the delayed evaluation of `f` with variables `x` and keyword args `kw`. The syntax for building such an object is `f[x1,x2,...,xn,k1=v1,k2=v2,...,km=vm]`, i.e., indexing a function with the fixed arguments and keyword arguments. Like an array, using `!` will leave a blank for extra arguments to be supplied on call.

Examples:

```
`sin[1.0]() == sin(1.0)`

`map[!,[1,2,3]](x->x+1) == map(x->x+1,[1,2,3])`

`map[!][[1,2,3]]() == map(x->x+1,[1,2,3])`

`sort[by=x->x[1]]([(2,:a),(1,:b)]) == sort([(2,:a),(1,:b)];by=x->x[1])`
```
