```
mutable struct TessInst
    ptr::Ptr{Cvoid}
end
```

A wrapper for the Api object in the Tesseract library.

**Values:**

| Name | Description                                               |
|:---- |:--------------------------------------------------------- |
| ptr  | The pointer to the Api object allocated by the C library. |

**Details:**

Most method calls cannot use this object until `tess_init()` called on it for initialization.

When the garbage collector collects this object the associated pointer object will be freed in the library.  The object can also be manually freed by calling `tess_delete!()` on it.

See also: [`TessInst(languages::AbstractString, dataPath::AbstractString)`](@ref).
