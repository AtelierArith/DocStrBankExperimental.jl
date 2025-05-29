```
argmaxima(x[, w=1; strict=true]) -> Vector{Int}
```

`x`の局所最大値のインデックスを見つけます。各最大値`i`は、`x[i-w:i+w]`の最大値または平坦な部分の最初のインデックスです。

平坦な部分は、連続した等しい(`==`)最大値を持ち、その前後に小さい値で囲まれた最大値として定義されます。

`strict == true`の場合、`x[i-w:i+w]`の要素は`missing`または`NaN`であってはならず、平坦な部分の境界が存在する必要があります。`strict == false`の場合、最大値は`x[i-w:i+w]`のすべての非`NaN`または`missing`要素の最大値であり、平坦な部分の境界は存在すると見なされます（すなわち、`missing`、`NaN`、または配列のいずれかの端、`x[begin-1]`または`x[end+1]`は平坦な部分の境界として扱われることがあります）。

参照: [`findmaxima`](@ref), [`findnextmaxima`](@ref), [`argminima`](@ref)

# 例

```jldoctest
julia> argmaxima([0,2,0,1,1,0])
2-element Vector{Int64}:
 2
 4

julia> argmaxima([2,0,1,1])
Int64[]

julia> argmaxima([2,0,1,1]; strict=false)
2-element Vector{Int64}:
 1
 3
```
