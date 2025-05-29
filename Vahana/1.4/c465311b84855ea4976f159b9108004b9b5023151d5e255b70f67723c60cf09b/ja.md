```
read_edges!(sim::Simulation, [name::String = sim.filename; idmapfunc = identity, transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
read_edges!(sim::Simulation, nr::Int64; [ idmapfunc = identity, transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
```

シミュレーション `sim` にHDF5ファイルからエッジを読み込みます。`name` が指定されている場合、エッジは現在の作業ディレクトリの `h5` サブフォルダ内のこのファイル名のファイルから読み込まれます。そうでない場合は、[`create_simulation`](@ref) 呼び出しからのファイル名が使用されます。

[`create_simulation`](@ref) の `overwrite_file` 引数が true に設定されている場合、ファイル名には番号が付加され、意図されたファイルの番号は `nr` 引数を介して指定できます。

デフォルトでは、ファイルに書き込まれた最後の遷移関数からエッジの状態が読み込まれます。`transition` キーワードを使用すると、以前のバージョンも読み込むことができます。あるいは、`write_snapshot` が呼び出されたときに指定されたコメントを `comment` キーワードで指定することで、対応するスナップショットを読み込むことができます。

特定のエッジタイプのサブセットのみを読み込む場合、このサブセットはオプションの `types` 引数を介して指定できます。

分散シミュレーションからエッジを単一スレッドのシミュレーションに読み込むと、エージェントのIDが変更されます。`idmapfunc` は、与えられた古いエージェントIDに対して新しいエージェントIDを返す関数でなければなりません。[`read_agents!`](@ref) は、これを使用するための `Dict{AgentID, AgentID}` を返します：`idmapfunc = (key) -> idmapping[key]`、ここで `idmapping` はそのような `Dict` です。
