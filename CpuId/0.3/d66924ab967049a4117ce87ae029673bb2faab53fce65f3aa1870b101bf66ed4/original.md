```
cacheinclusive()
cacheinclusive(lvl::Integer)
```

Obtain information on the CPU's *data* cache inclusiveness. Returns `true` for a cache that is inclusive of the lower cache levels, and `false` otherwise.

Determine the data cache size for each cache level as reported by the CPU using a set of calls to the `cpuid` instruction.  Returns a tuple with the tuple indices matching the cache levels.

If given an integer, then the data cache inclusiveness of the respective cache level will be returned.  This is significantly faster than the tuple version above.
