```
pydict(x)
pydict(; x...)
```

Convert `x` to a Python `dict`. In the second form, the keys are strings.

If `x` is a Python object, this is equivalent to `dict(x)` in Python. Otherwise `x` must iterate over key-value pairs.
