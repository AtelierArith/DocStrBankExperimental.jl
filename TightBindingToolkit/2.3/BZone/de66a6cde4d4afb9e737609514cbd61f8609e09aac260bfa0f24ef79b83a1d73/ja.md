`BZ`は、運動量空間における離散化されたブリルアンゾーンを表すデータ型です。

# 属性

  * `basis           :: Vector{ Vector{ Float64 } }`: ブリルアンゾーンの逆格子ベクトル。
  * `gridSize        :: Vector{Int64}`: グリッドの各次元に沿った点の数。
  * `kInds           :: Vector{Array{Float64}}`: bsに沿ったkに対応する[`Monkhorst`](@ref)グリッド。
  * `ks   	       :: Array{Vector{Float64}}`: 運動量ベクトルkのグリッド。
  * `HighSymPoints   :: Dict`: 高対称点Γ、K(2)、およびM(3)を含む辞書。
  * `shift           :: Vector{Int64}` : Γ点での中心点からグリッドがどれだけシフトしているか、`1/gridSize`の単位で。

この構造体を初期化するには、次のようにします。

```julia
BZ(gridSize::Int64) --> defaults to dims = 2
BZ(gridSize::Int64, dims) --> Uniform grid in dimension = dims
BZ(gridSize::Vector{Int64})
```
