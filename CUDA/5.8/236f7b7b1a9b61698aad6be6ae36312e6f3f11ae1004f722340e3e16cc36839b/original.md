```
for ...
    @captured begin
        # code that executes several kernels or CUDA operations
    end
end
```

A convenience macro for recording a graph of CUDA operations and automatically cache and update the execution. This can improve performance when executing kernels in a loop, where the launch overhead might dominate the execution.

!!! warning
    For this to be effective, the kernels and operations executed inside of the captured region should not signficantly change across iterations of the loop. It is allowed to, e.g., change kernel arguments or inputs to operations, as this will be processed by updating the cached executable graph. However, significant changes will result in an instantiation of the graph from scratch, which is an expensive operation.


See also: [`capture`](@ref).
