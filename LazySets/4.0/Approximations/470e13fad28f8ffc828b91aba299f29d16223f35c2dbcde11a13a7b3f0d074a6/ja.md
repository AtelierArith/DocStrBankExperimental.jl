```
BoxDiagDirections{N, VN} <: AbstractDirections{N, VN}
```

ボックス対角方向の表現。

### フィールド

  * `n` – 次元

### 注意事項

ボックス対角方向は、対角方向（すべてのエントリが±1）とボックス方向（1つのエントリが±1、他のすべてのエントリが0）の和集合と見なすことができます。イテレータは最初にすべての対角方向を列挙し、その後すべてのボックス方向を列挙します。次元 $n$ において、合計で $2^n + 2n$ の方向があります（例外：$n = 1$ の場合、方向は $2$ です）。

## 例

テンプレートは次元を渡すことで構築できます。たとえば、2次元の場合：

```jldoctest dirs_BoxDiag
julia> dirs = BoxDiagDirections(2)
BoxDiagDirections{Float64, Vector{Float64}}(2)

julia> length(dirs) # 方向の数
8
```

デフォルトでは、各方向は通常のベクトルとして表現されます：

```jldoctest dirs_BoxDiag
julia> eltype(dirs)
Vector{Float64} (alias for Array{Float64, 1})
```

2次元では、方向は八角形の面に対して法線であり、すなわちテンプレートは [`OctDirections`](@ref) と一致します。

```jldoctest dirs_BoxDiag
julia> collect(dirs)
8-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [-1.0, 1.0]
 [1.0, -1.0]
 [-1.0, -1.0]
 [1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]
 [-1.0, 0.0]
```

数値型も指定できます：

```jldoctest
julia> dirs = BoxDiagDirections{Rational{Int}}(10)
BoxDiagDirections{Rational{Int64}, Vector{Rational{Int64}}}(10)

julia> length(dirs)
1044
```
