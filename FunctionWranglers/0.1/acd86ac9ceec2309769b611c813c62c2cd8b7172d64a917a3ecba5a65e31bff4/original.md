```
sindex(wrangler::FunctionWrangler, idx, args...)
```

Call the `idx`-th function with args.

Note that this call iterates the wrangler from 1 to `idx`. Try to put the frequently called functions at the beginning to minimize overhead.
