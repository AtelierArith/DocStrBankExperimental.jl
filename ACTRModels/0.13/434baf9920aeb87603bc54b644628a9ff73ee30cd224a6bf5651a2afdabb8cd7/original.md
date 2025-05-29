```
Declarative(;memory=, filtered=(:isa,:retrieved))
```

Declarative memory module

# Fields

  * `memory=Chunk[]`: array of chunks
  * `filtered`: slots that must match exactly even when partial matching is on. By default,    `filtered=(:isa,:retrieved)`
  * `buffer`: an array containing one chunk
  * `state`: buffer state
