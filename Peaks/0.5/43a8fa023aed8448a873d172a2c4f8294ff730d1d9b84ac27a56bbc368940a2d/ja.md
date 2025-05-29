```
argminima(x[, w=1; strict=false]) -> Vector{Int}
```

`x`の局所的な最小値のインデックスを見つけます。各最小値`i`は、`x[i-w:i+w]`の最小値であるか、または高い値に挟まれた平坦な部分の最初のインデックスです。

平坦な部分は、連続した等しい（`==`）最小値を持ち、その連続した最小値の直前と直後により大きな値がある場合に定義されます。

`strict == true`の場合、`x[i-w:i+w]`内の要素は`missing`または`NaN`であってはならず、平坦な部分の境界が存在しなければなりません。`strict == false`の場合、最小値は`x[i-w:i+w]`内のすべての非`NaN`または`missing`要素の最小値であり、平坦な部分の境界は存在すると見なされます（すなわち、`missing`、`NaN`、または配列のいずれかの端、`x[begin-1]`または`x[end+1]`は平坦な部分の境界として扱われることがあります）。

参照: [`findminima`](@ref), [`findnextminima`](@ref)

# 例

```jldoctest
julia> argminima([3,2,3,1,1,3])
2-element Vector{Int64}:
 2
 4

julia> argminima([2,3,1,1])
Int64[]

julia> argminima([2,3,1,1]; strict=false)
2-element Vector{Int64}:
 1
 3
```
