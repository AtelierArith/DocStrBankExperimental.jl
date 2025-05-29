```
put!(algo::AbstractImageReconstructionAlgorithm, inputs...)
```

Perform image reonstruction with algorithm `algo` on given `ìnputs`. Depending on the algorithm this might block. Result is stored and can be retrieved with `take!`.
