```
function alloc_segbuf(domain_type=Float64, range_type=Float64, error_type=Float64; size=1)
```

This helper will allocate a segment buffer for segments to a `quadgk(...)` call with the given `domain_type`, which is the same as the type of the integration limits, `range_type` i.e. the range of the function being integrated and `error_type`, the type returned by the `norm` given to `quadgk(...)` and starting with the given `size`. The buffer can then be reused across multiple compatible calls to `quadgk(...)` to avoid repeated allocation.

Alternatively, you can replace your first call to `quadgk(...)` with a call to `quadgk_segbuf(...)`, which returns the computed segment buffer from your first integration.  This saves you the trouble of figuring out `domain_type` etc., which may not be obvious if the integrand is a variable.
