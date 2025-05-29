```
cpubrand()
```

Determine the cpu brand as a string as provided by the CPU through executing the `cpuid` instruction.  This function throws if no CPU brand information is available form the CPU, which should never be the case on recent hardware.
