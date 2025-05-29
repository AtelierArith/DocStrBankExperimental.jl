```
@critical expr
```

Mark code in `expr` as a critical section. Code in critical sections will never be executed in parallel (via multithreading) to any other critical section.

`@critical` is very useful to mark non-threadsafe code.

Example:

```julia
@onthreads allthreads() begin
    @critical @info Base.Threads.threadid()
end

Without `@critical`, the above will typically crash Julia.
```
