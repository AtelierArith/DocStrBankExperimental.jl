```
@pyeval [inputs =>] code [=> T]
```

Evaluate the given `code` in a new local scope and return the answer as a `T`.

The global scope is persistent and unique to the current module.

The `code` must be a literal string or command.

The `inputs` is a tuple of inputs of the form `v=expr` to be included in the local scope. Only `v` is required, `expr` defaults to `v`.

# Examples

The following computes `1.1+2.2` and returns a `Float64`:

```
@pyeval (x=1.1, y=2.2) => `x+y` => Float64  # returns 3.3
```
