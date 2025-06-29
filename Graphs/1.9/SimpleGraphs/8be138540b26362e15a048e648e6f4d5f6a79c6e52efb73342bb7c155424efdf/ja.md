```
rem_vertex!(g, v)
```

グラフ `g` から頂点 `v` を削除します。削除に失敗した場合（例えば、頂点がグラフに存在しない場合）は `false` を返し、それ以外の場合は `true` を返します。

### パフォーマンス

時間計算量は $\mathcal{O}(k^2)$ であり、ここで $k$ は頂点 `v` と頂点 $|V|$ の次数の最大値です。

### 実装ノート

この操作は、グラフ内のエッジや頂点によってインデックス付けされた外部データ構造を保持する場合は注意して実行する必要があります。内部的には、頂点 `v` と $|V|$ を入れ替え、最後の頂点 $|V|$ をグラフから削除することで行われます。削除後、`g` 内の頂点は $1:|V|-1$ でインデックス付けされます。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> rem_vertex!(g, 2)
true

julia> rem_vertex!(g, 2)
false
```
