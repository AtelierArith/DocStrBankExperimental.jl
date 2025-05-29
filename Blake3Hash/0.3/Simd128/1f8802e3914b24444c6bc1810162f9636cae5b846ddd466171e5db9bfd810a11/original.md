```
digest(self::Blake3Ctx, bytes=32)::Vector{UInt8}
```

Generate the hash and return it.

**Details:**

Normally you would want 32 bytes back (256bits) but you can have it return more or less bytes based on your need.
