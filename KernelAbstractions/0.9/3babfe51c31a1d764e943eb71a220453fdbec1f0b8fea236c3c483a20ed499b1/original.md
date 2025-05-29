```
@Const(A)
```

`@Const` is an argument annotiation that asserts that the memory reference by `A` is both not written to as part of the kernel and that it does not alias any other memory in the kernel.

!!! danger
    Violating those constraints will lead to arbitrary behaviour.

    As an example given a kernel signature `kernel(A, @Const(B))`, you are not allowed to call the kernel with `kernel(A, A)` or `kernel(A, view(A, :))`.

