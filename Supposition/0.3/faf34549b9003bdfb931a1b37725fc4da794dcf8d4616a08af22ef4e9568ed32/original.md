```
reject!()
```

Reject the current testcase as invalid, meaning the generated example should not be considered as producing a valid counterexample.

!!! warning "Callability"
    This can only be called while a testcase is currently being examined or an example for a `Possibility` is being actively generated. It is ok to call this inside of `@composed` or `@check`, as well as any functions only intended to be called from one of those places.

