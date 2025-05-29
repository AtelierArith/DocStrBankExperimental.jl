```
digest(self::Blake3Ctx, out_slice::AbstractArray{UInt8})::Nothing
```

Generate the hash and write it to the provided array.  The contents of out_slice will be overwritten.

**Details:**

Normally you would pass in an array of 32 bytes which the method will fill with the hash. However if you want more (or less) bytes you can pass in a an array of a different size.
