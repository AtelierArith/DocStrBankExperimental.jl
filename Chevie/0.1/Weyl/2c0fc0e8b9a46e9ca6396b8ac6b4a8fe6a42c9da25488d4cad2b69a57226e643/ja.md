`coxeter_group(type,rank[,bond];sc=false)` (または `coxgroup`)

もし `C=cartan(type,rank[,bond])` の場合、これは `rootdatum(C)` と同等です。もし `sc=true` の場合、これは `rootdatum(permutedims(C),one(C))` と同等です。

結果として得られるオブジェクト `W` は、`PermRootGroup` と比較して追加のエントリを持つ `FiniteCoxeterGroup` です。

  * `W.rootdec`: 簡単な根の線形結合として与えられる根ベクトル。最初の `nref(W)` 根は正の根であり、次の `nref(W)` 根は対応する負の根です。さらに、最初の `semisimplerank(W)` 根は簡単な根です。正の根は高さが増加する順に並べられています。

そして `roots(W)` は `W.rootdec` と同じ順序で並べられています。

根系とコクセター群に関するさまざまな情報を取得する方法については、関数 `nref, coroots, rootlengths, simple_reps, simple_conjugating, reflrep, simpleroots, simplecoroots, PermX, cartan, inclusion, restriction, action, rank, semisimplerank` を参照してください。

根データの観点から、この関数はウィール群 `W` の随伴根データを返します。もし `sc=true` の場合、単連結根データを返します。

```julia_repl
julia> W=coxgroup(:G,2)
G₂

julia> cartan(W)
2×2 Matrix{Int64}:
  2  -1
 -3   2

julia> W.rootdec
12-element Vector{Vector{Int64}}:
 [1, 0]
 [0, 1]
 [1, 1]
 [1, 2]
 [1, 3]
 [2, 3]
 [-1, 0]
 [0, -1]
 [-1, -1]
 [-1, -2]
 [-1, -3]
 [-2, -3]

julia> reflrep(W)
2-element Vector{Matrix{Int64}}:
 [-1 0; 1 1]
 [1 3; 0 -1]
```
