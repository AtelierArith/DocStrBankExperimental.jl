```
cpu_bus_frequency()
```

Determine the bus CPU frequency in MHz as reported directly from the CPU through a `cpuid` instrauction call.  Returns zero if the CPU doesn't provide bus frequency information.
