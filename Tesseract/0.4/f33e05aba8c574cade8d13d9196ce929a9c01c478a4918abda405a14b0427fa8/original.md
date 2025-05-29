```
mutable struct Pix
    ptr::Ptr{Cvoid}
end
```

A wrapper for the PIX structure in the leptonica library.

**Values:**

| Name | Description                                               |
|:---- |:--------------------------------------------------------- |
| ptr  | The pointer to the Pix object allocated by the C library. |

**Details:**

When the garbage collector collects this object the associated PIX object will be freed in the library.
