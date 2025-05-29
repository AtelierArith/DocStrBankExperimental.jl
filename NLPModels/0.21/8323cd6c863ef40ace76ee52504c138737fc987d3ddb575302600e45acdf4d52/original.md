```
nls_meta(nls)
```

Returns the `nls_meta` structure of `nls`. Use this instead of `nls.nls_meta` to handle models that have internal models.

For basic models `nls_meta(nls)` is defined as `nls.nls_meta`, but composite models might not keep `nls_meta` themselves, so they might specialize it to something like `nls.internal.nls_meta`.
