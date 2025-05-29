```
write_errors(errf, errors) → errored::Bool
```

Saves backtraces of errors into a file.

# Arguments

  * `errf`: File where errors will be saved.
  * `errors`: Array of backtraces

# Returns

  * `errored`: `false` if `errors` was an empty array.

Function `write_errors` is public, not exported.
