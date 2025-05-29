```
canonical_gauge(pso::PSOModel)
canonical_gauge(bbox::Blackbox)
```

Apply an invertible transformation that takes the model to coordinates in which `P` is `[I ; 0]` (up to floating point errors). Note this will create a dense model.
