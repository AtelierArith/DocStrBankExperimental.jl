```
address_size()
```

Determine the maximum virtual address size supported by this CPU as reported by the `cpuid` instructions.

This information may be used to determine the number of high bits that can be used in a pointer for tagging;  viz. `sizeof(Int) - address_size() ÷ 8`, which gives on most 64 bit Intel machines 2 bytes = 16 bit for other purposes.
