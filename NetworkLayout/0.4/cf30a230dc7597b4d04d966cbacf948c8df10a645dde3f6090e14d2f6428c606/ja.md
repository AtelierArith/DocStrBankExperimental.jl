```
Shell(; kwargs...)(adj_matrix)
shell(adj_matrix; kwargs...)
```

同心円にノードを配置します。追加の引数がない場合、すべてのノードは半径1.0の円に配置されます。ノードの配置は`nlist`引数を使用して指定します。

ネットワークの隣接行列表現を受け取り、ノードの座標を返します。

## キーワード引数

  * `Ptype=Float64`: 出力タイプ`Point{2,Ptype}`を決定します。
  * `nlist=Vector{Int}[]`

    ノードインデックスのベクトルのベクトル。アルゴリズムに、どのノードを内側から外側のシェルに配置するかを指示します。このリストに存在しないノードは、追加の最外シェルに配置されます。

この関数は[IainNZ](https://github.com/IainNZ)の[GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl)からのコピーとして始まりました。
