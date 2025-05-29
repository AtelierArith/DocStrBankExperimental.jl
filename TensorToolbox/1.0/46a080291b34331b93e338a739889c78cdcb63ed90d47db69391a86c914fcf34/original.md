---

```
contract(T::TTtensor,X::Array,start_mode,modes)
```

Contract modes 1:ndims(X-1) of full tensor X to TTtensor T cores[start*mode:start*mode+modes-1]. Output: TTtensor.
