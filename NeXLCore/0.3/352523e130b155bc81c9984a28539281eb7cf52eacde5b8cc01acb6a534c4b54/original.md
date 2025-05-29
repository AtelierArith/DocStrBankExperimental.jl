```
has(elm::Element, tr::Transition)::Bool
```

Is the specified Transition available for the specified element?

Example:

```
@assert has(n"Fe L3-M5)
@assert !has(n"Fe N7-O9)
```
