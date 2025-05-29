セルは三次元空間における周期構造を表します。

定義は次のとおりです：

```julia
mutable struct Cell{T}
    lattice::Lattice{T}                 # 構造の格子
    symbols::Vector{Symbol}
    positions::Matrix{T}
    arrays::Dict{Symbol, Any}        # 追加の配列
    metadata::Dict{Symbol, Any}
end
```
