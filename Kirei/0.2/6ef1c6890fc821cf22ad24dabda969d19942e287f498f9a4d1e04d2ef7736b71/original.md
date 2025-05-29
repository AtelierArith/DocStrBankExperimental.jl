```
@target [os=(windows, linux, macos)] [arch=(x86_64, aarch64, ...)] expr
```

Evaluate `expr` only when the target OS and architecture match the given conditions.

It uses `@static` to evaluate the conditions at parse time.
