```
check_efficient_action(
    source_file::AbstractString,
    source_line::Integer,
    operand::AbstractString,
    matrix::AbstractMatrix,
    axis::Integer,
)::Nothing
```

This will check whether the code about to be executed for an `operand` which is `matrix` works "with the grain" of the data, which requires the `matrix` to be in `axis`-major layout. If it isn't, then apply the [`inefficient_action_handler`](@ref). Typically this isn't invoked directly; instead use [`@assert_matrix`](@ref).

In general, you **really** want operations to go "with the grain" of the data. Unfortunately, Julia (and Python, and R, and matlab) will silently run operations "against the grain", which would be **painfully** slow. A liberal application of this function in your code will help in detecting such slowdowns, without having to resort to profiling the code to isolate the problem.

!!! note
    This will not prevent the code from performing "against the grain" operations such as `selectdim(matrix, Rows, 1)` for a column-major matrix, but if you add this check before performing any (series of) operations on a matrix, then you will have a clear indication of whether such operations occur. You can then consider whether to invoke [`relayout!`](@ref) on the data, or (for data fetched from `Daf`), simply query for the other memory layout.

