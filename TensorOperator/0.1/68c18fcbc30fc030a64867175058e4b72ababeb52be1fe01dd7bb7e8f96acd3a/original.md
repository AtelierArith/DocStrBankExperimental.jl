```
BaseTensor(e...)
```

The constructor for first-order base tensors with components `e`. The corresponding component is defaultly set to be `1.0`. Only first-order base tensors can be implemented by this function, i.e. `order = 1`, the high order ones can be constructed by dyadic operator `⊗`. The dimension of base tensor depends on the length of inputed components, i.e. `dim = length(e)`.
