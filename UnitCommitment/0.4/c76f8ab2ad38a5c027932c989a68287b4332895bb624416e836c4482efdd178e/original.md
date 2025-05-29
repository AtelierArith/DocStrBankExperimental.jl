```
repair!(sc)
```

Verifies that the given unit commitment scenario is valid and automatically fixes some validation errors if possible, issuing a warning for each error found. If a validation error cannot be automatically fixed, issues an exception.

Returns the number of validation errors found.
