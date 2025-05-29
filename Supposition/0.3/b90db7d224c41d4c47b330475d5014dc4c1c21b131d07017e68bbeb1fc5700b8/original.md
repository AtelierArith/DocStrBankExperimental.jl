```
target!(score)
```

Update the currently running testcase to track the given score as its target.

`score` must be `convert`ible to a `Float64`.

!!! danger "Multiple Updates"
    This score can only be set once! Repeated calls will be ignored.


!!! warning "Callability"
    This can only be called while a testcase is currently being examined or an example for a `Possibility` is being actively generated. It is ok to call this inside of `@composed` or `@check`, as well as any functions only intended to be called from one of those places.

