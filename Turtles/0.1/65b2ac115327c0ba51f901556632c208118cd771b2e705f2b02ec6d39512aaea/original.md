```
@proc [ret] function name() end
```

Transforms function into `@code` block that calls `IR.proc`. If the function is recursive, the return type `ret` must be provided
