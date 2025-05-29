```
physical_address_size()
```

Determine the maximum phyiscal addresses size supported by this CPU as reported by the `cpuid` instructions.  Prefer to make use of `address_size` for practical purposes; use this only for diagnostic issues, such as determining the theoretical maximum memory size.  Also note that this address size is manipulated by a running hypervisor.
