```
input_type([P=Direct,] A)
output_type([P=Direct,] A)
```

yield the (preferred) types of the input and output arguments of the operation `P` with mapping `A`.  If `A` operates on Julia arrays, the element type, list of dimensions, `i`-th dimension and number of dimensions for the input and output are given by:

```
input_eltype([P=Direct,] A)          output_eltype([P=Direct,] A)
input_size([P=Direct,] A)            output_size([P=Direct,] A)
input_size([P=Direct,] A, i)         output_size([P=Direct,] A, i)
input_ndims([P=Direct,] A)           output_ndims([P=Direct,] A)
```

For mappings operating on Julia arrays, only `input_size(A)` and `output_size(A)` have to be implemented.

Also see: [`vcreate`](@ref), [`apply!`](@ref), [`LinearMapping`](@ref), [`Operations`](@ref).
