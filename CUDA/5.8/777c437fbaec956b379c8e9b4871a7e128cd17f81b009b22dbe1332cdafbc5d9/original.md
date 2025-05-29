```
unsafe_reset!(pctx::CuPrimaryContext)
```

Explicitly destroys and cleans up all resources associated with a device's primary context in the current process. Note that this forcibly invalidates all contexts derived from this primary context, and as a result outstanding resources might become invalid.
