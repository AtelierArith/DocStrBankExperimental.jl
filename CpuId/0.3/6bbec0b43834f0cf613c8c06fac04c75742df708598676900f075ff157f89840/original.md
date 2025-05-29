```
cpu_max_frequency()
```

Determine the maximum CPU frequency in MHz as reported directly from the CPU through a `cpuid` instrauction call.  The maximum frequency typically refers to the CPU's boost frequency.  Returns zero if the CPU doesn't provide maximum frequency information.
