```julia
allgraphs(
    n::Vector{Int64};
    connected
) -> Vector{Tuple{Vector{Pair{Int64, Int64}}, Float64}}

```

与えられた頂点仕様に対してすべてのユニークなトポロジーを生成します。`n[k]`が次数`k`の頂点の数であるベクターを入力として受け取ります。デフォルトでは、接続されたグラフを生成し、キーワード引数`connected=false`を設定することで非接続グラフを計算できます。

`Edge`がグラフ内のエッジを表す`Tuple{Int64,Int64}`であり、`S::Float64`が対応する対称因子であるタプル`(Vector{Edge}, S)`のベクターを返します。

## 例

入力`n = [2, 0, 0, 2]`（次数1の頂点2つ、次数4の頂点2つ）の場合：

```jldoctest
julia> using GraphCombinations

julia> allgraphs([2, 0, 0, 2])
3-element Vector{Tuple{Vector{Pair{Int64, Int64}}, Float64}}:
 ([1 => 3, 2 => 3, 3 => 4, 3 => 4, 4 => 4], 4.0)
 ([1 => 3, 2 => 4, 3 => 3, 3 => 4, 4 => 4], 4.0)
 ([1 => 3, 2 => 4, 3 => 4, 3 => 4, 3 => 4], 6.0)
```
