```
read_agents!(sim::Simulation, [name::String = sim.filename; transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
read_agents!(sim::Simulation, nr::Int64; [transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
```

シミュレーション `sim` にHDF5ファイルからエージェントを読み込みます。`name` が指定されている場合、エージェントは現在の作業ディレクトリの `h5` サブフォルダからこのファイル名のファイルから読み込まれるか、[`set_hdf5_path`](@ref) で設定されたサブフォルダから読み込まれます。そうでない場合は、[`create_simulation`](@ref) 呼び出しからのファイル名が使用されます。

[`create_simulation`](@ref) の `overwrite_file` 引数が true に設定されており、ファイル名に番号が付加される場合、`nr` 引数を介して対象のファイルの番号を指定できます。

デフォルトでは、ファイルに書き込まれた最後の遷移関数からエージェントの状態が読み込まれます。`transition` キーワードを使用すると、以前のバージョンも読み込むことができます。あるいは、`write_snapshot` が呼び出されたときに指定されたコメントを `comment` キーワードで指定することで、対応するスナップショットを読み込むことができます。

特定のエージェントタイプのサブセットのみを読み込む場合、このサブセットはオプションの `types` 引数を介して指定できます。

分散シミュレーションからエージェントを単一スレッドのシミュレーションに読み込むと、エージェントのIDが変更されます。 `read_agents!` はIDマッピングを含む辞書を返します。
