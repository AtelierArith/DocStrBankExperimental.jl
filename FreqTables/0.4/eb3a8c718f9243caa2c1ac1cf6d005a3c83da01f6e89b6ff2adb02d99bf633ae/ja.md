```
freqtable(x::AbstractVector...;
          skipmissing::Bool = false,
          weights::AbstractVector{<:Real} = UnitWeights(),
          subset::Union{Nothing, AbstractVector{Int}, AbstractVector{Bool}} = nothing])

freqtable(t, cols::Union{Symbol, AbstractString}...;
          skipmissing::Bool = false,
          weights::AbstractVector{<:Real} = UnitWeights(),
          subset::Union{Nothing, AbstractVector{Int}, AbstractVector{Bool}} = nothing])
```

ベクトルまたはテーブルの列から頻度表を作成します。

`t` は [Tables.jl](https://github.com/JuliaData/Tables.jl) インターフェースでサポートされている任意のタイプのテーブルです。

**例**

```jldoctest
julia> freqtable([1, 2, 2, 3, 4, 3])
4-element Named Array{Int64,1}
Dim1  │ 
──────┼──
1     │ 1
2     │ 2
3     │ 2
4     │ 1

julia> df = DataFrame(x=[1, 2, 2, 2], y=[1, 2, 1, 2]);

julia> freqtable(df, :x, :y)
2×2 Named Array{Int64,2}
x ╲ y │ 1  2
──────┼─────
1     │ 1  0
2     │ 1  2

julia> freqtable(df, :x, :y, subset=df.x .> 1)
1×2 Named Array{Int64,2}
x ╲ y │ 1  2
──────┼─────
2     │ 1  2

```
