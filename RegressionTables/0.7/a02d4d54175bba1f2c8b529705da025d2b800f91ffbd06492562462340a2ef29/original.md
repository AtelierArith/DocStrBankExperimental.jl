```
mutable struct RegressionTable{T<:AbstractRenderType} <: AbstractMatrix{String}
    data::Vector{DataRow{T}}
    align::String
    render::T
    breaks::Vector{Int}
    colwidths::Vector{Int}
    vertical_gaps::Vector{Int}
end

RegressionTable(header::Vector, body::Matrix, args...; vargs...)
RegressionTable(
    header::Matrix,
    body::Matrix,
    render::T=AsciiTable();
    breaks=[size(header, 1)],
    align='l' * 'r' ^ (size(header, 2) - 1),
    colwidths=fill(0, size(header, 2)),
    header_align='l' * 'c' ^ (size(header, 2) - 1),
    extralines::Vector = DataRow[]
) where T<:AbstractRenderType
```

The general container. This provides some general information about the table. The [`DataRow`](@ref) handles the main printing, but this provides other necessary information, especially the `break` field, which is used to determine where to put the lines (e.g., `\midrule` in LaTeX).

  * `data`: A vector of [`DataRow`](@ref) objects.
  * `align`: A string of characters, one for each column, indicating the alignment of the column. The characters are   `l` for left, `c` for center, and `r` for right.
  * `render`: The render type of the table. This must be the same as the render type of the [`DataRow`](@ref) objects and is used for convenience.
  * `breaks`: A vector of integers, indicating where to put the lines (e.g., `\midrule` in LaTeX). When displayed, the break will be placed after  the line number is printed (breaks = [5] will print a break after the 5th line is printed).
  * `colwidths`: A vector of integers, one for each column, indicating the width of the column. Can calculate the widths   automatically using [`calc_widths`](@ref) and update them with [`update_widths!`](@ref).
  * `vertical_gaps`: A vector of integers, indicating where to put vertical gaps in the table. These are places where two underlined cells   are not connected. This is necessary for Excel integration.

The `RegressionTable` is a subtype of the `AbstractMatrix{String}` type (though this functionality is somewhat experimental). Importantly, this implements `getindex` and `setindex!`, which means individual elements of the table can be modified after its construction. See examples below. It also allows a `RegressionTable` to be passed to a function that expects a matrix, for example, exporting to a `DataFrame` [DataFrames.jl](https://github.com/JuliaData/DataFrames.jl) would be `DataFrame(Matrix(tab), :auto)`. Note that this will not keep multicolumn, unerlines, etc. information, but could be useful for exporting to other formats.

This type also has two convenience constructors which might be helpful if using this package to print summary statistics.

## Example

```jldoctest; setup=:(using RegressionTables, RDatasets, DataFrames)
julia> df = RDatasets.dataset("datasets", "iris");

julia> df = describe(df, :mean, :std, :q25, :median, :q75; cols=["SepalLength", "SepalWidth", "PetalLength", "PetalWidth"]);

julia> t = RegressionTables.RegressionTable(names(df), Matrix(df))
 
----------------------------------------------------
variable       mean    std     q25    median    q75
----------------------------------------------------
SepalLength   5.843   0.828   5.100    5.800   6.400
SepalWidth    3.057   0.436   2.800    3.000   3.300
PetalLength   3.758   1.765   1.600    4.350   5.100
PetalWidth    1.199   0.762   0.300    1.300   1.800
----------------------------------------------------

julia> t[1, 2] = "Mean of Variable";

julia> t[2, 3] = 0;

julia> RegressionTables.update_widths!(t); # necessary if a column gets longer

julia> t
 
---------------------------------------------------------------
variable      Mean of Variable    std     q25    median    q75
---------------------------------------------------------------
SepalLength              5.843       0   5.100    5.800   6.400
SepalWidth               3.057   0.436   2.800    3.000   3.300
PetalLength              3.758   1.765   1.600    4.350   5.100
PetalWidth               1.199   0.762   0.300    1.300   1.800
---------------------------------------------------------------
```
