```
rmresource(T)
```

Remove `T` from the list of available resources. For example, `rmresource(OpenCLLibs)` would indicate that any future package loads should avoid loading their specializations for OpenCL.
