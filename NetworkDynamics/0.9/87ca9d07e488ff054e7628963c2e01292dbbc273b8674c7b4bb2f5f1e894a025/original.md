```
abstract type ExecutionStyle{buffered::Bool} end
```

Abstract type for execution style. The coreloop dispatches based on the Execution style stored in the network object.

  * `buffered=true` means that the edge input es explicitly gathered, i.e. the vertex outputs in the output buffer will be copied into a dedicated input buffer for the edges.
  * `buffered=false` means, that the edge inputs are not explicitly gathered, but the corloop will perform a redirected lookup into the output buffer.
