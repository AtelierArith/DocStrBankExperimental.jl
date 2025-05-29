```
read_snapshot!(sim::Simulation, [name::String; transition = typemax(Int64), comment = "", writeable = false, ignore_params = false])
read_snapshot!(sim::Simulation, nr::Int64; [transition = typemax(Int64), comment = "", writeable = false, ignore_params = false])
```

シミュレーション `sim` にファイルから完全なスナップショットを読み込みます。`name` が指定されている場合、スナップショットは現在の作業ディレクトリの `h5` サブフォルダからこのファイル名のファイルから読み込まれます。別の場合は、[`create_simulation`](@ref) 呼び出しからのファイル名が使用されます。

[`create_simulation`](@ref) の `overwrite_file` 引数が true に設定されている場合、ファイル名に番号が補足され、意図されたファイルの番号は `nr` 引数を介して指定できます。

デフォルトでは、最後に書き込まれたスナップショットが読み込まれます。`transition` キーワードを使用すると、以前のバージョンも読み込むことができます。あるいは、`write_snapshot` が呼び出されたときに指定されたコメントを `comment` キーワードで指定して、対応するスナップショットを読み込むことができます。

`writeable` が true に設定されている場合、ファイルはシミュレーションに添付され、[`write_snapshot`](@ref) のような次の `write_` 関数はファイルに追加されます。

`ignore_params` が true に設定されている場合、`sim` のパラメータは変更されません。

スナップショットが見つからなかった場合は false を返します。
