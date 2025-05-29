```
cpu_base_frequency()
```

Determine the CPU nominal base frequency in MHz as reported directly from the CPU through a `cpuid` instruction call.  Returns zero if the CPU doesn't provide base frequency information.

The actual cpu frequency might be lower due to throttling, or higher due to frequency boosting (see `cpu_max_frequency`).
