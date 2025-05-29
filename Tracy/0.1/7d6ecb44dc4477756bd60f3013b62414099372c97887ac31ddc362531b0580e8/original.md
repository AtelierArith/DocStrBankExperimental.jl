```
Tracy
```

The `Tracy` module provides the `@tracepoint` macro which can be used to create scoped regions for profiling with Tracy.

`@tracepoint`s can be runtime enabled/disabled with `enable_tracepoint` or they can be erased from the generated code entirely using invalidation with `configure_tracepoint`. The latter is effectively a "compile-time" enable/disable for tracing zones for ultra-low overhead.

If Julia was built with the compile-time flag `WITH_TRACY` enabled, the recorded traces will also include data from various parts of the Julia runtime, including codegen, GC, and runtime-internal mutexes/locks.
