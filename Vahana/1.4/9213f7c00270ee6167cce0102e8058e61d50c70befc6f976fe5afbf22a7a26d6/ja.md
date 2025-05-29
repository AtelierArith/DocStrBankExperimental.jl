```
create_h5file!(sim::Simulation, [filename = sim.filename; overwrite = sim.overwrite_file])
```

HDF5ファイルを作成する標準的な方法は、[`write_snapshot`](@ref)のような`write_`関数のいずれかを呼び出すことです。`sim`にまだHDF5ファイルが添付されていない場合、そのファイルは[`create_simulation`](@ref)で指定されたキーワードのファイル名を使用して自動的に作成されます。また、このキーワードが指定されていない場合は、モデル名が使用されます。しかし、[`copy_simulation`](@ref)の呼び出し後など、手動でこれを制御することが有用な場合もあります。

`filename`引数は、`sim.filename`以外のファイル名を指定するために使用できます。`overwrite`がtrueの場合、この名前の既存のファイルは上書きされます。falseの場合、ファイル名は自動的に増加する6桁の数字で拡張され、既存のファイルは上書きされません。

デフォルトでは、ファイルは`h5`サブフォルダーに作成され、これは現在の作業ディレクトリに作成されます。ただし、パスは`set_hdf5_path`関数を使用して設定することもできます。

シミュレーション`sim`のためにHDF5ファイルがすでに作成されている場合、これが閉じられます。

`create_h5file!`は、[`finish_init!`](@ref)の後にのみ呼び出すことができます。

また、[`close_h5file!`](@ref)、[`write_agents`](@ref)、[`write_edges`](@ref)、[`write_globals`](@ref)、[`read_agents!`](@ref)、[`read_edges!`](@ref)、[`read_globals`](@ref)、[`read_snapshot!`](@ref)および[`list_snapshots`](@ref)も参照してください。
