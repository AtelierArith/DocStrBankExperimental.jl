```
running_median!(mf::MedianFilter, output, input, tapering=:sym; nan=:include) -> output
```

Use `mf` to calculate the running median of `input` and write the result to `output`.

For all details, see [`running_median`](@ref).

# Examples

```jldoctest
input = [4 5 6;
         1 0 9;
         9 8 7;
         3 1 2;]
output = similar(input, (4,3))
mf = MedianFilter(eltype(input), 3)
for j in axes(input, 2) # run median over each column
    # re-use mf in every iteration
    running_median!(mf, @view(output[:,j]), input[:,j])
end
output

# output
4×3 Matrix{Int64}:
 4  5  6
 4  5  7
 3  1  7
 3  1  2
```
