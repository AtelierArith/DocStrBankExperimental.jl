グループ内の単純体に近い単純体に対して `f` をマップします。

```julia
mapSimplexElements(
        f,
        output,
        s::SimplexCellList,
        x::Simplex{N},
        group_idx::Integer,
        elements_type::Type{Simplex{M}},
        cutoff::Float32,
    ) where {N, M}
```

関数 `f` を単純体 `x` のカットオフ範囲内のグループ `group_idx` のすべての要素に適用し、最終的な `f` 呼び出しの出力を返します。

`x` は常に `x` であり、`i` は常に 0 です。

### マップされた関数 `f`

関数 f は CellListMap.jl で使用されるのと同じ形式である必要があります。

`i` は単純体 `x` の要素インデックス、`j` は単純体 `y` の要素インデックスです。

`d2` は `x` と `y` の間の近似 `Float32` の二乗距離です。

ここでは `x` と `y` は `Simplex{N}`、`Simplex{M}` です。

```julia
    function f(x,y,i,j,d2,output)
        # 出力を更新
        return output
    end
```
