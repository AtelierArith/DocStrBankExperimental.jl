任意の安定器状態をグラフ状態に変換する

[グラフ状態](https://en.wikipedia.org/wiki/Graph_state)は、グラフによって表現できる特別なタイプのエンタングルされた安定器状態です。グラフ $G=(V,E)$ に対して、対応する安定器は $S_v = X_v \prod_{u ∈ N(v)} Z_u$ です。このような表の行には、単一の X 演算子のみが含まれていることに注意してください。任意の安定器状態をグラフ状態に変換するための単一量子ビットゲートのセットがあります。

この関数は、安定器に対応するグラフ状態と、安定器をグラフとして表現可能な状態に変換するために必要なゲートを返します。

表 `stab` を次のように変換できます：

```julia
graph, hadamard_idx, iphase_idx, flips_idx = graphstate()
```

ここで `graph` は `stab` のグラフ表現であり、残りは `stab` を `graph` に変換するための単一量子ビットゲートを指定します：`hadamard_idx` は Hadamard ゲートが必要な量子ビット（X ↔ Z のマッピング）、`iphase_idx` は逆位相ゲートが必要な（異なる）量子ビット（Y → X）、`flips_idx` は前の2つのゲートの後に位相反転（パウリ Z ゲート）が必要な量子ビットです。

```jldoctest graph
julia> using Graphs

julia> s = S" XXX
              ZZ_
             -_ZZ";


julia> g, h_idx, ip_idx, z_idx = graphstate(s);


julia> collect(edges(g))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3

julia> h_idx
2-element Vector{Int64}:
 2
 3

julia> ip_idx
Int64[]

julia> z_idx
1-element Vector{Int64}:
 3
```

`Graphs.jl` ライブラリは多くのグラフ理論ツールを提供し、`MakieGraphs.jl` ライブラリはグラフのプロットユーティリティを提供します。

安定器に対してグラフコンストラクタを直接呼び出すことができます。もしグラフだけが欲しく、任意の状態をグラフとして表現可能な状態に変換するために必要なクリフォード操作を気にしない場合は、次のようにします：

```jldoctest graph
julia> collect(edges( Graph(bell()) ))
1-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
```

安定器をコピーせず、むしろインプレースで変換を行うバージョンを使用するには、`graphstate!` を使用します。これは、グラフ状態に変換する方法を見つけると、引数に対して `canonicalize_gott!` を実行します。
