```
create_partitioning_file(LaMEM_input::String, NumProc::Int64; LaMEM_dir::String=pwd(), LaMEM_options::String="", MPI_dir="", verbose=true)
```

これは、入力ファイル `LaMEM_input` に対して LaMEM を実行し、`NumProc` プロセッサ用の並列パーティショニングファイルを作成します。LaMEM バイナリがあるディレクトリを指定することができ、指定しない場合は現在のディレクトリにあると仮定されます。同様に、`mpiexec` ディレクトリについても（指定しない場合はコマンドラインで利用可能であると仮定されます）。
