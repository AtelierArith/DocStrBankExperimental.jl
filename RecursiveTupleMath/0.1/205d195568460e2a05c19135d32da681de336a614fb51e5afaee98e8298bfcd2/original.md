Implements broadcasting functions that operate elementwise and recursively across `Tuple`s, `NamedTuple`s, `SArray`s, and `ForwardDiff.Dual` numbers.

```
The functions are:
- `badd` (broadcast add)
- `bsub` (broadcast sub)
- `bmul` (broadcast mul)
- `bdiv` (broadcast div)
- `bmax` (broadcast max)
- `bmin` (broadcast min)
```

Note that because it is recursive, `bmul(a, b)` will not necessarilly do the same thing as `map(*, a, b)`. For example, if `a` and `b` are tuples of `SMatrices`, `bmul` will multiply them elementwise, while `map` will multiply them as matrices. This is because `bmul` will call `bmul` on the elements of `a` and `b`, while `map` will call `*` on the elements of `a` and `b`.
