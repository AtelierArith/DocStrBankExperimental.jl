```
anyof(f, args...) -> bool
```

checks whether predicate function `f` returns `true` for any argument `args...`, returning `true` as soon as possible (short-circuiting).

```
anyof(args...) -> bool
```

checks whether all arguments `args...` are `true`, returning `false` as soon as possible (short-circuiting). Arguments can be booleans or arrays of booleans. The latter are considered as `true` if any of their elements are `true` and are considered as `false` otherwise (if all their elements are `false`). Arguments can also be iterables to check whether any of their values are `true`. An empty iterable is considered as `false`.

This method can be much faster than `any(f, args)` or `any(args)` because its result may be determined at compile time. However, `missing` values are not considered as special.

See also `any`, [`allof`](@ref), [`noneof`](@ref).
