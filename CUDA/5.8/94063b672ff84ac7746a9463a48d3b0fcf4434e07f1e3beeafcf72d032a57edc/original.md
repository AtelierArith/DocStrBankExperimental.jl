```
capture([flags], [throw_error::Bool=true]) do
    ...
end
```

Capture a graph of CUDA operations. The returned graph can then be instantiated and executed repeatedly for improved performance.

Note that many operations, like initial kernel compilation or memory allocations, cannot be captured. To work around this, you can set the `throw_error` keyword to false, which will cause this function to return `nothing` if such a failure happens. You can then try to evaluate the function in a regular way, and re-record afterwards.

See also: [`instantiate`](@ref).
