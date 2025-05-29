```
allof(f, args...) -> Bool
```

checks whether predicate function `f` returns `true` for all arguments in `args...`, returning `false` as soon as possible (short-circuiting).

```
allof(args...) -> Bool
```

checks whether all arguments `args...` are `true`, returning `false` as soon as possible (short-circuiting). Arguments can be booleans or arrays of booleans. The latter are considered as `true` if all their elements are `true` and are considered as `false` otherwise (if any of their elements are `false`). Arguments can also be iterables to check whether all their values are `true`. An empty iterable is considered as `true`.

This method can be much faster than `all(f, args)` or `all(args)` because its result may be determined at compile time. However, `missing` values are not considered as special.

See also `all`, [`anyof`](@ref), [`noneof`](@ref).
