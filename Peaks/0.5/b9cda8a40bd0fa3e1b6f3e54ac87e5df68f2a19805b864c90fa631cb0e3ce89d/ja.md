```
findminima(x[, w=1; strict=true]) -> (;indices, heights, data)
```

`x`の局所的な最小値のインデックスと値を見つけます。各最小値`i`は、`x[i-w:i+w]`の最小値であるか、または高原の最初のインデックスです。

`indices`、`heights`、`data`というフィールドを含む`NamedTuple`を返します。これは`heights = data[indices]`に相当します。`data`フィールドは引数`x`への参照（コピーではありません）です。

高原は、連続した等しい（`==`）最小値が、連続した最小値の直前と直後により大きな値で囲まれている最小値として定義されます。

関連情報: [`argminima`](@ref), [`findnextminima`](@ref)

# 例

```jldoctest
julia> data = [1, 5, 1, 3, 2];

julia> valleys = findminima(data)
(indices = [3], heights = [1], data = [1, 5, 1, 3, 2])
```
