```
Tensor(lvl)
```

Construct a `Tensor` using the tensor level storage `lvl`. No initialization of storage is performed, it is assumed that position 1 of `lvl` corresponds to a valid tensor, and `lvl` will be wrapped as-is. Call a different constructor to initialize the storage.
