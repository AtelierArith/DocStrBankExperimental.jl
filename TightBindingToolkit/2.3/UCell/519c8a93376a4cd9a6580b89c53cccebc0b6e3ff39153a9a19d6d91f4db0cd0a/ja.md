`UnitCell{T}` は格子の一般的な単位セルを表すデータ型です。

# 属性

  * `primitives  :: Vector{ Vector{ Float64 } }`: 格子の原始基底ベクトル。
  * `basis       :: Vector{ Vector{ Float64 } }`: サブ格子の位置。
  * `bonds       :: Vector{Bond{T}}`: 格子を定義するすべてのボンドの集合。
  * `fields      :: Vector{ Vector{Float64}}` : 各基底サイトの場。
  * `localDim    :: Int64`: ローカルヒルベルト空間の次元（例：古典スピンの場合は3、スピン-1/2電子の場合は2）。
  * `BC          :: Vector{ ComplexF64 }`: 境界条件、形式は [e^{ιθ_i}]。例：PBCの場合はθ=0、APBCの場合はθ=πなど。

この構造体は次のように初期化します。

```julia
UnitCell( as::Vector{Vector{Float64}} , localDim::Int64)
UnitCell( as::Vector{Vector{Float64}} , localDim::Int64, rank::Int64)
```
