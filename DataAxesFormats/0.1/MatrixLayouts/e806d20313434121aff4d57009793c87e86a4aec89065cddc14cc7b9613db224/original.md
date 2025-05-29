All stored `Daf` matrix data has a clear matrix layout, that is, a [`major_axis`](@ref), regardless of whether it is dense or sparse.

That is, for [`Columns`](@ref)-major data, the values of each column are laid out consecutively in memory (each column is a single contiguous vector), so any operation that works on whole columns will be fast (e.g., summing the value of each column). In contrast, the values of each row are stored far apart from each other, so any operation that works on whole rows will be very slow in comparison (e.g., summing the value of each row).

For [`Rows`](@ref)-major data, the values of each row are laid out consecutively in memory (each row is a single contiguous vector). In contrast, the values of each column are stored far apart from each other. In this case, summing columns would be slow, and summing rows would be fast.

This is much simpler than the [ArrayLayouts](https://github.com/JuliaLinearAlgebra/ArrayLayouts.jl) module which attempts to fully describe the layout of N-dimensional arrays, a much more ambitious goal which is an overkill for our needs.

!!! note
    The "default" layout in Julia is column-major, which inherits this from matlab, which inherits this from FORTRAN, allegedly because this is more efficient for some linear algebra operations. In contrast, Python `numpy` uses row-major layout by default. In either case, this is just an arbitrary convention, and all systems work just fine with data of either memory layout; the key consideration is to keep track of the layout, and to apply operations "with the grain" rather than "against the grain" of the data.

