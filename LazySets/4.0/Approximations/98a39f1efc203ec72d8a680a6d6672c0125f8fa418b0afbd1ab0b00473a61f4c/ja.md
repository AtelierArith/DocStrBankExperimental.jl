```
DiagDirections{N, VN} <: AbstractDirections{N, VN}
```

対角方向の表現。

### フィールド

  * `n` – 次元

### ノート

対角方向は、すべてのエントリが ±1 のベクトルです。次元 $n$ では、合計で $2^n$ の方向があります。

## 例

テンプレートは次元を渡すことで構築できます。たとえば、次元が2の場合：

```jldoctest dirs_Diag
julia> dirs = DiagDirections(2)
DiagDirections{Float64, Vector{Float64}}(2)

julia> length(dirs) # 方向の数
4
```

デフォルトでは、各方向は通常の `Vector` として表現されます：

```jldoctest dirs_Diag
julia> eltype(dirs)
Vector{Float64} (alias for Array{Float64, 1})
```

2次元では、`DiagDirections` によって定義された方向は、1ノルムのボールの面に対して法線です。

```jldoctest dirs_Diag
julia> collect(dirs)
4-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [-1.0, 1.0]
 [1.0, -1.0]
 [-1.0, -1.0]
```

数値型も指定できます：

```jldoctest
julia> dirs = DiagDirections{Rational{Int}}(10)
DiagDirections{Rational{Int64}, Vector{Rational{Int64}}}(10)

julia> length(dirs)
1024
```
