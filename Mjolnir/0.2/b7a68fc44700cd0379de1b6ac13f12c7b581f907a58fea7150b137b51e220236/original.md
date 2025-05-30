```
@trace f(args...)
@trace P f(args...)
```

Get a typed trace for `f`, analagous to `@code_typed`. Note that unlike `@code_typed`, you probably want to pass types rather than values, e.g.

```
julia> @trace ::Int + ::Int
1: (%1 :: const(+), %2 :: Int64, %3 :: Int64)
  %4 = (+)(%2, %3) :: Int64
  return %4
```

If you instead pass actual integers, Mjolnir will aggressively constant-propagate them, resulting in a trivial trace.

```
julia> @trace 2+2
1: (%1 :: const(+), %2 :: const(2), %3 :: const(2))
  return 4
```

`P` is the primitive set used, which is `Mjolnir.Defaults()` by default.
