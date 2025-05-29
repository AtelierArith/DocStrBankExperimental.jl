```
get_tmp_cache(i::DEIntegrator)
```

Returns a tuple of internal cache vectors which are safe to use as temporary arrays. This should be used for integrator interface and callbacks which need arrays to write into in order to be non-allocating. The length of the tuple is dependent on the method.
