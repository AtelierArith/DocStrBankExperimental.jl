```
pyjlraw(v)
```

Create a Python object wrapping the Julia object `x`.

It has type `juliacall.RawValue`. This has a much more rigid "Julian" interface than `pyjl(v)`. For example, accessing attributes or calling this object will always return a `RawValue`.
