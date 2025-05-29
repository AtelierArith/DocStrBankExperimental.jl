```
findmaxima(x[, w=1; strict=true]) -> (;indices, heights, data)
```

`x`の局所最大値のインデックスと値を見つけます。各最大値`i`は、`x[i-w:i+w]`の最大値であるか、またはプラトーの最初のインデックスです。

`indices`、`heights`、`data`というフィールドを含む`NamedTuple`を返します。これは`heights = data[indices]`に相当します。`data`フィールドは引数`x`への参照（コピーではありません）です。

プラトーは、連続した等しい（`==`）最大値を持ち、その連続した最大値の直前と直後により小さい値で制約される最大値として定義されます。

参照: [`argmaxima`](@ref), [`findnextmaxima`](@ref), [`findminima`](@ref)

# 例

```jldoctest
julia> data = [1, 5, 1, 3, 2];

julia> pks = findmaxima(data)
(indices = [2, 4], heights = [5, 3], data = [1, 5, 1, 3, 2])
```
