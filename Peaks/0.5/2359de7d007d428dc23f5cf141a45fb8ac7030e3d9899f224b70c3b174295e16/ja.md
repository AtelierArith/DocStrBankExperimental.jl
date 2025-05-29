```
findnextmaxima(x, i[, w=1; strict=true]) -> Int
```

`i`を含む`x`の次の最大値のインデックスを見つけます。ここで、最大値`i`は`x[i-w:i+w]`の最大値であるか、または高原の最初のインデックスです。`i`の後に最大値が存在しない場合は`lastindex(x) + 1`を返します。

高原は、連続した等しい（`==`）最大値を持つ最大値であり、連続した最大値の直前と直後により小さい値で制約されています。

`strict == true`の場合、`x[i-w:i+w]`の要素に`missing`または`NaN`が含まれてはならず、高原の境界が存在する必要があります。`strict == false`の場合、最大値は`x[i-w:i+w]`のすべての非`NaN`または`missing`要素の最大値であり、高原の境界は存在すると仮定されます（すなわち、`missing`、`NaN`、または配列のいずれかの端、`x[begin-1]`または`x[end+1]`は高原の境界として扱われることがあります）。

参照: [`argmaxima`](@ref)

# 例

```jldoctest
julia> findnextmaxima([0,2,0,1,1,0], 2)
2

julia> findnextmaxima([0,2,0,1,1,0], 3)
4

```
