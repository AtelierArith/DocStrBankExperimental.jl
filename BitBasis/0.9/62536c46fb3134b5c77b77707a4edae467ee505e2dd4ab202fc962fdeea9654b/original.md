```
reorder(X::AbstractArray, orders)
```

Reorder `X` according to `orders`.

!!! tip
    Although `orders` can be any iterable, `Tuple` is preferred inorder to gain as much performance as possible. But the conversion won't take much anyway.

