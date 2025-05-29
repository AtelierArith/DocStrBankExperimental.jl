```
from_dlpack(o)
```

If `o` follows the DLPack specification, it returns a zero-copy `array::AbstractArray` pointing to the same data in `o`. For arrays with row-major ordering the resulting array will have all dimensions reversed.
