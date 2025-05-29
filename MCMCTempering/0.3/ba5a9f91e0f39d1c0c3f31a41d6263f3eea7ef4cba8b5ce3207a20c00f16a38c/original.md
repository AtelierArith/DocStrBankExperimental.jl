```
SingleRandomSwap <: AbstractSwapStrategy
```

At every swap step taken, this strategy samples two chain indices `i` and 'j' and proposes a swap between the two corresponding chains.

This approach is shown to be effective for certain models in [^1].

[^1]: Malcolm Sambridge, A Parallel Tempering algorithm for probabilistic sampling and multimodal optimization, Geophysical Journal International, Volume 196, Issue 1, January 2014, Pages 357–374, https://doi.org/10.1093/gji/ggt342
