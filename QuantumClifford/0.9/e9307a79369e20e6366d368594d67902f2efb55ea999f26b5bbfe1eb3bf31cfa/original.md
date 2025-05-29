Convert a tableau to a memory layout that is fast for column operations.

In this layout a column of the tableau is stored (mostly) contiguously in memory. Due to bitpacking, e.g., packing 64 bits into a single `UInt64`, the memory layout is not perfectly contiguous, but it is still optimal given that some bitwrangling is required to extract a given bit.

See also: [`fastrow`](@ref)
