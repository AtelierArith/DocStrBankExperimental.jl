```
finish(interp::AbstractInterpreter, opt::OptimizationState,
       ir::IRCode, caller::InferenceResult)
```

Post-process information derived by Julia-level optimizations for later use. In particular, this function determines the inlineability of the optimized code.
