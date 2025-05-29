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

一般的なコンテナです。これはテーブルに関する一般的な情報を提供します。[`DataRow`](@ref)は主な印刷を処理しますが、これは特に`break`フィールドなど、必要な他の情報を提供します。これは、行をどこに置くかを決定するために使用されます（例：LaTeXの`\midrule`）。

  * `data`: [`DataRow`](@ref)オブジェクトのベクター。
  * `align`: 各列の整列を示す文字の文字列。文字は、左揃えのための`l`、中央揃えのための`c`、右揃えのための`r`です。
  * `render`: テーブルのレンダリングタイプ。これは[`DataRow`](@ref)オブジェクトのレンダリングタイプと同じでなければならず、便利のために使用されます。
  * `breaks`: 行をどこに置くかを示す整数のベクター（例：LaTeXの`\midrule`）。表示されると、ブレークは行番号が印刷された後に配置されます（breaks = [5]は5行目が印刷された後にブレークを印刷します）。
  * `colwidths`: 各列の幅を示す整数のベクター。[`calc_widths`](@ref)を使用して幅を自動的に計算し、[`update_widths!`](@ref)で更新できます。
  * `vertical_gaps`: テーブル内の垂直ギャップをどこに置くかを示す整数のベクター。これは、2つの下線付きセルが接続されていない場所です。これはExcel統合に必要です。

`RegressionTable`は`AbstractMatrix{String}`型のサブタイプです（ただし、この機能はやや実験的です）。重要なのは、`getindex`と`setindex!`を実装しているため、テーブルの個々の要素は構築後に変更できます。以下の例を参照してください。また、`RegressionTable`を行列を期待する関数に渡すことも可能で、たとえば、`DataFrame` [DataFrames.jl](https://github.com/JuliaData/DataFrames.jl)にエクスポートする場合は`DataFrame(Matrix(tab), :auto)`になります。これはマルチカラム、下線などの情報を保持しませんが、他の形式にエクスポートする際に便利です。

この型には、要約統計を印刷するためにこのパッケージを使用する場合に役立つかもしれない2つの便利なコンストラクタもあります。

## 例

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

julia> RegressionTables.update_widths!(t); # 列が長くなる場合は必要

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
