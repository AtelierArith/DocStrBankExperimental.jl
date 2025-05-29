```
maybe_static(f, args...)
```

Returns `static(f(args...))`, if all of `args` are `Static` and `f` returns a number. If any of the args is not `Static`, then `f(args...)` is returned unchanged.

The `@stat` macro applies the `maybe_static` function to all function calls, and this function can be overloaded to provide special behaviuor for certain functions under the macro.
