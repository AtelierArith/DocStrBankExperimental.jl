```
waive!(r, res_request)
waive!(q, request)
```

Allows to remove first occurence that would be served of `res_request` from `SimResource` or `request` from `SimQueue`.

Returns `true` on success and `false` if `res_request` or `request` respectively was not found.
