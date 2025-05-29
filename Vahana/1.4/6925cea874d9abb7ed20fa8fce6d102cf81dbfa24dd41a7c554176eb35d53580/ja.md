```
read_params(filename::String, T::DataType)
read_params(sim::Simulation, T::DataType)
read_params(sim::Simulation, nr::Int64, T::DataType)
read_params(filename::String)
```

HDF5ファイルからパラメータを読み込みます。`filename`が指定されている場合、パラメータは現在の作業ディレクトリの`h5`サブフォルダにあるこのファイル名のファイルから読み込まれます。

代わりにシミュレーション`sim`が指定されている場合、[`create_simulation`](@ref)呼び出しからのファイル名が使用されます。

[`create_simulation`](@ref)の`overwrite_file`引数がtrueに設定されており、ファイル名に番号が補足されている場合、意図されたファイルの番号は`nr`引数を介して指定できます。

シミュレーションに使用される[`create_simulation`](@ref)の引数`globals`のDataType `T`が指定されている場合、結果はTのインスタンスになります。それ以外の場合は、書き込まれたGlobals型のフィールドをキーとするDictになります。
