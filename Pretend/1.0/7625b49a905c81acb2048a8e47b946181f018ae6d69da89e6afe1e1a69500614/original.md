```
spy(f::Function)
```

Run the function without any patches. Using `spy` is more efficient than [`apply`](@ref) due to the zero patch overhead.
