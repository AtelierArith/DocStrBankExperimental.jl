```
addmul!(z, a, b, t)
addmul!(z, a, b)
```

Return `z + a * b`, possibly modifying the objects `z` and `t` in the process.

The second version is usually a shorthand for `addmul!(z, a, b, parent(z)())`, but in some cases may be more efficient. For multiple operations in a row that use temporary storage, it is still best to use the four argument version.
