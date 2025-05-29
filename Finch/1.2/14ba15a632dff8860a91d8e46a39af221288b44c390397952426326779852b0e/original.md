```
lazy(arg)
```

Create a lazy tensor from an argument. All operations on lazy tensors are lazy, and will not be executed until `compute` is called on their result.

for example,

```julia
x = lazy(rand(10))
y = lazy(rand(10))
z = x + y
z = z + 1
z = compute(z)
```

will not actually compute `z` until `compute(z)` is called, so the execution of `x + y` is fused with the execution of `z + 1`.
