```
cachesize()
cachesize(lvl::Integer)
```

Obtain information on the CPU's *data* cache sizes.

Determine the data cache size for each cache level as reported by the CPU using a set of calls to the `cpuid` instruction.  Returns a tuple with the tuple indices matching the cache levels; sizes are given in bytes.

If given an integer, then the data cache size of the respective cache level will be returned.  This is significantly faster than the tuple version above.

Note that these are total cache sizes, where some cache levels are typically shared by multiple cpu cores, the higher cache levels may include lower levels. To print the cache levels in kbyte, use e.g. `CpuId.cachesize() .÷ 1024`.

This functions throws an error if cache size detection is not supported.
