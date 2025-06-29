```
findnextminima(x, i[, w=1, strict=true]) -> Int
```

`x`の中で、`i`の後または`i`を含む次の最小値のインデックスを見つけます。ここで、最小値`i`は`x[i-w:i+w]`の最小値であるか、または高い値に挟まれた平坦な部分の最初のインデックスです。`i`の後に最小値が存在しない場合は`lastindex(x) + 1`を返します。

平坦な部分は、連続した等しい（`==`）最小値を持つ最小値として定義され、連続した最小値の直前と直後により大きな値に挟まれています。

`strict == true`の場合、`x[i-w:i+w]`の中に`missing`または`NaN`の要素があってはならず、平坦な部分の境界が存在しなければなりません。`strict == false`の場合、最小値は`x[i-w:i+w]`の中のすべての非`NaN`または`missing`要素の最小値であり、平坦な部分の境界は存在すると仮定されます（すなわち、`missing`、`NaN`、または配列のいずれかの端、`x[begin-1]`または`x[end+1]`は平坦な部分の境界として扱われることがあります）。

参照: [`argminima`](@ref)

# 例

```jldoctest
julia> findnextminima([3,2,3,1,1,3], 2)
2

julia> findnextminima([3,2,3,1,1,3], 3)
4

```
