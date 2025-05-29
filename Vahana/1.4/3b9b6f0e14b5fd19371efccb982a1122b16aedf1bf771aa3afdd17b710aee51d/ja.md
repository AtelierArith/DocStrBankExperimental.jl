```
read_globals(filename::String, T::DataType; [ transition = typemax(Int64), comment = "" ])
read_globals(sim::Simulation, T::DataType; [ transition = typemax(Int64), comment = "" ])
read_globals(sim::Simulation, nr::Int64, T::DataType; [ transition = typemax(Int64), comment = "" ])
read_globals(filename::String; [ transition = typemax(Int64), comment = "" ])
```

HDF5ファイルからグローバル値を読み取ります。`filename`が指定されている場合、パラメータは現在の作業ディレクトリの`h5`サブフォルダにあるこのファイル名のファイルから読み取られます。

代わりにシミュレーション`sim`が指定されている場合、[`create_simulation`](@ref)呼び出しからのファイル名が使用されます。

[`create_simulation`](@ref)の`overwrite_file`引数がtrueに設定されており、ファイル名に番号が補足されている場合、`nr`引数を介して対象のファイルの番号を指定できます。

シミュレーションに使用される[`create_simulation`](@ref)の引数`globals`のDataType `T`が指定されている場合、結果はTのインスタンスになります。それ以外の場合は、書き込まれたGlobals型のフィールドをキーとするDictになります。

デフォルトでは、最後に書き込まれたグローバルが読み取られます。`transition`キーワードを使用すると、以前のバージョンも読み取ることができます。代わりに、write_snapshotが呼び出されたときに指定されたコメントを`comment`キーワードで指定することで、対応するスナップショットを読み取ることができます。

詳細については、[File storage](./hdf5.md)も参照してください。
