```julia
Table(;
    content,
    offset_x::Real = 50,
    offset_y::Real = 50,
    size_x::Real = 150,
    size_y::Real = 100,
    column_widths::Vector{<:Real}, # 列ごとのサイズを設定
    row_heights::Vector{<:Real}, # 行ごとのサイズを設定
    header::Bool = true, # 列名をヘッダーとして自動的に書き込むかどうか
    bandrow::Bool = true, # 行ごとに交互に色を使うかどうか
)
```

スライドで使用するためのテーブル。

内容は `Tables.jl` インターフェースに準拠するものであれば何でも可能です。

オフセットとサイズはミリメートルで指定されますが、EMUに変換されます。

各セルを個別にスタイル設定するには `TableCell` を参照してください。

# 例

```jldoctest
julia> using PPTX, DataFrames

julia> df = DataFrame(a = [1,2], b = [3,4], c = [5,6])
2×3 DataFrame
 Row │ a      b      c     
     │ Int64  Int64  Int64 
─────┼─────────────────────
   1 │     1      3      5
   2 │     2      4      6

julia> t = Table(content=df, size_x=30)
Table
 content isa DataFrames.DataFrame
 offset_x is 1800000 EMUs
 offset_y is 1800000 EMUs
 size_x is 1080000 EMUs
 size_y is 3600000 EMUs

```
