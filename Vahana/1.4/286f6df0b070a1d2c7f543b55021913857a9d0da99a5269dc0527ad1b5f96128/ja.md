```
list_snapshots(name::String)
list_snapshots(sim::Simulation)
list_snapshots(sim::Simulation, nr::Int64)
```

HDF5ファイルのすべてのスナップショットをリストします。`name`が指定されている場合は、このファイル名のスナップショットが返されます。そうでない場合は、[`create_simulation`](@ref)呼び出しからファイル名が使用されます。

[`create_simulation`](@ref)の`overwrite_file`引数がtrueに設定されている場合、ファイル名に番号が補足され、`nr`引数を介して対象のファイルの番号を指定できます。

戻り値はタプルのベクターで、最初の要素はスナップショットが保存された遷移番号であり、2番目の要素は[`write_snapshot`](@ref)呼び出しで与えられたコメントです。
