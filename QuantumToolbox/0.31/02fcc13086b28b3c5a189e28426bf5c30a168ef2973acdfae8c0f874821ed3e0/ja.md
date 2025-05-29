```
struct EigsolveResult
```

固有値、固有ベクトル、およびソルバーからの情報を含む構造体

# フィールド（属性）

  * `values::AbstractVector`: 固有値
  * `vectors::AbstractMatrix`: 変換行列（固有ベクトル）
  * `type::Union{Nothing,QuantumObjectType}`: [`QuantumObject`](@ref) のタイプ、または `nothing` は一般行列の固有方程式を解くことを意味します
  * `dimensions::Union{Nothing,AbstractDimensions}`: [`QuantumObject`](@ref) の `dimensions`、または `nothing` は一般行列の固有方程式を解くことを意味します
  * `iter::Int`: 解決プロセス中の反復回数
  * `numops::Int` : krylov メソッドで線形写像が適用された回数
  * `converged::Bool`: 結果が収束したかどうか

!!! note "`dims` プロパティ"
    与えられた `res::EigsolveResult` に対して、`res.dims` または `getproperty(res, :dims)` は整数ベクトルの型でその `dimensions` を返します。


# 例

固有値と対応する [`QuantumObject`](@ref) タイプの固有ベクトルを取得するには、次のようにします：

```jldoctest
julia> result = eigenstates(sigmax())
EigsolveResult:   type=Operator()   dims=[2]
values:
2-element Vector{ComplexF64}:
 -1.0 + 0.0im
  1.0 + 0.0im
vectors:
2×2 Matrix{ComplexF64}:
 -0.707107+0.0im  0.707107+0.0im
  0.707107+0.0im  0.707107+0.0im

julia> λ, ψ, U = result;

julia> λ
2-element Vector{ComplexF64}:
 -1.0 + 0.0im
  1.0 + 0.0im

julia> ψ
2-element Vector{QuantumObject{Ket, Dimensions{1, Tuple{Space}}, Vector{ComplexF64}}}:

Quantum Object:   type=Ket()   dims=[2]   size=(2,)
2-element Vector{ComplexF64}:
 -0.7071067811865475 + 0.0im
  0.7071067811865475 + 0.0im

Quantum Object:   type=Ket()   dims=[2]   size=(2,)
2-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im

julia> U
2×2 Matrix{ComplexF64}:
 -0.707107+0.0im  0.707107+0.0im
  0.707107+0.0im  0.707107+0.0im
```
