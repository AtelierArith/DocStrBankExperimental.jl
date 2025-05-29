```
@! func(args)
```

The `@!` macro calls `func(ctx, args)`, where `ctx` is the "current context" as created by the `@context` macro.  If `@!` is used outside a `@context` block, a warning is emitted and the global context is used.

---

```
@! function my_func(...)
    ...
end
```

This form adds a `context::AbstractContext` argument as the first argument to `my_func`. This allows the responsibility for resource cleanup to be passed back to the caller by using `@defer` within `my_func` or `@!` to further chain the resource handling.
