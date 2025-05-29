```
Replace(f, with)
Replace(f; with)
```

This postprocessor replaces all cell values for which `f(value) === true` with the value `with`. If `with <: Function` then the new value will be `with(value)`, instead.

## Examples

```
Replace(x -> x isa String, "A string was here")
Replace(x -> x isa String, uppercase)
Replace(x -> x isa Int && iseven(x), "An even Int was here")
```
