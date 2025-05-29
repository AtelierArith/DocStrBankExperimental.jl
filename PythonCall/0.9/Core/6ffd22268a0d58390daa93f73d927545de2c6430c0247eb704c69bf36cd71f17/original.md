```
@pyexec [inputs =>] code [=> outputs]
```

Execute the given `code` in a new local scope.

The global scope is persistent and unique to the current module.

The `code` must be a literal string or command.

The `inputs` is a tuple of inputs of the form `v=expr` to be included in the local scope. Only `v` is required, `expr` defaults to `v`.

The `outputs` is a tuple of outputs of the form `x::T=v`, meaning that `v` is extracted from locals, converted to `T` and assigned to `x`. Only `x` is required: `T` defaults to `Py` and `v` defaults to `x`.

# Examples

The following computes `1.1+2.2` and assigns its value to `ans` as a `Float64`:

```
@pyexec (x=1.1, y=2.2) => `ans=x+y` => ans::Float64  # returns 3.3
```

Marking variables as `global` saves them into the module scope, so that they are available in subsequent invocations:

```
@pyexec `global x; x=12`
@pyeval `x` => Int  # returns 12
```
