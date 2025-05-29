```
strongly_connected_components(g)
```

有向グラフ `g` の強連結成分を計算します。

接続された各成分全体を含む配列の配列を返します。

### 実装ノート

成分の順序はAPI契約の一部ではありません。

# 例

```jldoctest
julia> g = DiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> strongly_connected_components(g)
2-element Array{Array{Int64,1},1}:
 [3]
 [1, 2]
```
