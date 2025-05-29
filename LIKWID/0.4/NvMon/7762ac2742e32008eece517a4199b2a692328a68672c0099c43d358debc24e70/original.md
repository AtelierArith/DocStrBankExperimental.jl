```
@nvmon group_or_groups codeblock
```

See also: [`nvmon`](@ref)

**Note: This is an experimental feature and might change or be dropped any time!**

# Example

```
julia> using LIKWID

julia> x = CUDA.rand(1000); y = CUDA.rand(1000);

julia> metrics, events = @nvmon "FLOPS_DP" x .+ y;
```
