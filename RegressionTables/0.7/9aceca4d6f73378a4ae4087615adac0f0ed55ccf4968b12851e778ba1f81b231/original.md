```
mutable struct DataRow{T<:AbstractRenderType} <: AbstractVector{String}
    data::Vector
    align::String
    colwidths::Vector{Int}
    print_underlines::Vector{Bool}
    render::T
end

DataRow(x::DataRow) = x

(::Type{T})(x::DataRow) where {T<:AbstractRenderType} = DataRow(x.data, x.align, x.colwidths, x.print_underlines, T())

function DataRow(
    data::Vector,
    align,
    colwidths,
    print_underlines,
    render::AbstractRenderType;
    combine_equals=false
)

function DataRow(
    data::Vector;
    align="l" * "r" ^ (length(data) - 1),
    colwidths=fill(0, length(data)),
    print_underlines=zeros(Bool, length(data)),
    render::AbstractRenderType=AsciiTable(),
    combine_equals=false
)
```

DataRow forms the fundamental element of a RegressionTable. For a user, these can be passed as  additional elements to `group` or `extralines` in [`regtable`](@ref). A DataRow is typed with an [`AbstractRenderType`](@ref), which controls how the DataRow is displayed. The default is [`AsciiTable`](@ref). The DataRow contains four other elements:

  * `data::Vector`: The data to be displayed in the row. Can be individual elements (e.g., [1, 2, 3]) or pairs with a range  (e.g., [1 => 1:2, 2 => 3:4]), or a combination of the two.
  * `align::String`: A string of ('l', 'r', 'c'), one for each element of `data`, indicating that elements alignment.
  * `colwidths::Vector{Int}`: A vector of integers, one for each element of `data`, indicating the width of the column.  Can calculate the widths automatically using [`calc_widths`](@ref) and update them with [`update_widths!`](@ref).
  * `print_underlines::Vector{Bool}`: A vector of booleans, one for each element of `data`, indicating whether to print  an underline under the element. This is useful for printing the header of a table.

DataRow is a subtype of `AbstractVector{String}`. It implements `getindex` and `setindex!`, which allows changing of individual elements.

!!! note
    In most cases, it is not necessary to specify the render type for DataRow. While constructing a RegressionTable, the render type is changed to the render type of the RegressionTable.


## Examples

```jldoctest
julia> DataRow(["", "Group 1" => 2:3, "Group 2" => 4:5])
   Group 1   Group 2

julia> DataRow(["", "Group 1", "Group 1", "Group 2", "Group 2"]; combine_equals=true)
   Group 1   Group 2

julia> DataRow(["", "Group 1" => 2:3, "Group 2" => 4:5])
   Group 1   Group 2

julia> DataRow(["   ", "Group 1" => 2:3, "Group 2" => 4:5]; print_underlines=[false, false, true])
      Group 1   Group 2
                -------

julia> DataRow(["Group 0", "Group 1" => 2:3, "Group 2" => 4:5]; colwidths=[20, 20, 20], align="lcr", print_underlines=true)
Group 0                       Group 1                      Group 2
--------------------   --------------------   --------------------

julia> DataRow(["", "Group 1" => 2:3, "Group 2" => 4:5]; render=LatexTable())
 & \multicolumn{2}{r}{Group 1} & \multicolumn{2}{r}{Group 2} \\ 
```
