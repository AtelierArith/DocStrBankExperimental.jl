```
BeamSearch(bsize::Integer=16, Δ::Float32)
```

BeamSearch is an iteratively improving local search algorithm that explores the graph using blocks of `bsize` elements and neighborhoods at the time.

  * `bsize`: The size of the beam.
  * `Δ`: Soft margin for accepting elements into the beam
  * `maxvisits`: MAximum visits while searching, useful for early stopping without convergence
