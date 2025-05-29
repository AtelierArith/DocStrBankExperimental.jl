`f`を2つの異なるグループ間の近接するシンプレックスのすべてのペアにマップします。

```julia
mapElementsElements(
        f, 
        output, 
        s::SimplexCellList, 
        x_group_idx::Integer, 
        x_type::Type{Simplex{N}}, 
        y_group_idx::Integer, 
        y_type::Type{Simplex{M}}, 
        cutoff::Float32,
    ) where {N, M}
```

関数`f`を、互いにカットオフ範囲内にある2つの異なるグループの要素のペアに適用し、最終的な`f`呼び出しの出力を返します。

最初の要素はグループ`x_group_idx`の`x_type`であり、2番目の要素はグループ`y_group_idx`の`y_type`です。

`f`はペアごとに1回以上呼び出されることはありません。

### マップされた関数`f`

関数fはCellListMap.jlで使用されるのと同じ形式である必要があります。

`i`はシンプレックス`x`の要素インデックス、`j`はシンプレックス`y`の要素インデックスです。

`d2`は`x`と`y`の間の近似`Float32`の二乗距離です。

ここでは`x`と`y`は`Simplex{N}`、`Simplex{M}`です。

```julia
    function f(x,y,i,j,d2,output)
        # 出力を更新
        return output
    end
```
