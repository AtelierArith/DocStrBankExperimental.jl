```
@withcolor ex
```

Make sure that `ex` is evaluated while `Base.have_color` is set to `true`. The original value of `Base.have_color` will be restored afterwards.

This macro is particularily useful for CI, where it is not unusual that  `julia` is executed without the `--color=yes` argument by default.

```julia
@withcolor print_with_color(:green, "foo")
```
