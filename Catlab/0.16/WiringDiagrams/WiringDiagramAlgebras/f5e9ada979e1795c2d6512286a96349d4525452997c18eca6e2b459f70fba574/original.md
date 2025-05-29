Evaluate a conjunctive query on an attributed C-set.

The conjunctive query is represented as an undirected wiring diagram (UWD) whose boxes and ports are named via the attributes `:name`, `:port_name`, and `:outer_port_name`. To define such a diagram, use the [`@relation`](@ref) macro with its named syntax. Parameters to the query may be passed as a collection of pairs using the optional third argument.

The result is data table whose columns correspond to the outer ports of the UWD. By default, a data frame is returned if the package [`DataFrames.jl`](https://github.com/JuliaData/DataFrames.jl) is loaded; otherwise, a named tuple is returned. To change this behavior, set the keyword argument `table_type` to a type or function taking two arguments, a vector of columns and a vector of column names. There is one exceptional case: if the UWD has no outer ports, the query is a counting query and the result is a vector whose length is the number of results.

For its implementation, this function wraps the [`oapply`](@ref) method for multispans, which defines the UWD algebra of multispans.
