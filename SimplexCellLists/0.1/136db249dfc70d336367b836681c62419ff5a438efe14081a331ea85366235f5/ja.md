近くの単体のすべてのペアに `f` をマップします。

```julia
mapPairElements(
        f,
        output,
        s::SimplexCellList,
        group_idx::Integer,
        elements_type::Type{Simplex{N}},
        cutoff::Float32,
    ) where {N}
```

関数 `f` を、カットオフ範囲内のグループ `group_idx` の要素のすべての無順序ペアに適用し、最終的な `f` 呼び出しの出力を返します。

`f` は無順序ペアごとに一度だけ呼び出されます。`f` への呼び出しにおける要素 `x` と `y` のどちらがどちらであるかは実装に依存します。

### マップされた関数 `f`

関数 f は CellListMap.jl で使用されるのと同じ形式である必要があります。

`i` は単体 `x` の要素インデックス、`j` は単体 `y` の要素インデックスです。

`d2` は `x` と `y` の間の近似 `Float32` 二乗距離です。

ここでは `x` と `y` は `Simplex{N}`、`Simplex{M}` です。

```julia
    function f(x,y,i,j,d2,output)
        # 出力を更新
        return output
    end
```
