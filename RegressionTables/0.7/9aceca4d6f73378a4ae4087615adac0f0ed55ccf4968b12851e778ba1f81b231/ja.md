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

DataRowはRegressionTableの基本要素を形成します。ユーザーは、これらを[`regtable`](@ref)の`group`や`extralines`に追加要素として渡すことができます。DataRowは[`AbstractRenderType`](@ref)で型付けされており、DataRowの表示方法を制御します。デフォルトは[`AsciiTable`](@ref)です。DataRowは他に4つの要素を含みます：

  * `data::Vector`: 行に表示されるデータ。個々の要素（例： [1, 2, 3]）や範囲を持つペア（例： [1 => 1:2, 2 => 3:4]）、またはその二つの組み合わせが可能です。
  * `align::String`: `data`の各要素に対して1つずつ、要素の配置を示す ('l', 'r', 'c') の文字列。
  * `colwidths::Vector{Int}`: `data`の各要素に対して1つずつ、列の幅を示す整数のベクトル。[`calc_widths`](@ref)を使用して幅を自動的に計算し、[`update_widths!`](@ref)で更新できます。
  * `print_underlines::Vector{Bool}`: `data`の各要素に対して1つずつ、要素の下に下線を印刷するかどうかを示すブール値のベクトル。これはテーブルのヘッダーを印刷する際に便利です。

DataRowは`AbstractVector{String}`のサブタイプです。個々の要素を変更できるように`getindex`と`setindex!`を実装しています。

!!! note
    ほとんどの場合、DataRowのレンダータイプを指定する必要はありません。RegressionTableを構築する際、レンダータイプはRegressionTableのレンダータイプに変更されます。


## 例

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
