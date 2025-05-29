```
use_system_binary(;
    library_names = ["libmpi", "libmpi_ibm", "msmpi", "libmpich", "libmpi_cray", "libmpitrampoline"],
    extra_paths = String[],
    mpiexec = "mpiexec",
    abi = nothing,
    vendor = nothing,
    export_prefs = false,
    force = true)
```

システム提供のMPI実装に切り替えます。変更を有効にするにはJuliaを再起動する必要があります。

オプション:

  * `library_names`: [`Libdl.find_library`](https://docs.julialang.org/en/v1/stdlib/Libdl/#Base.Libc.Libdl.find_library)に渡されるMPIライブラリの名前または名前のコレクション。ライブラリがライブラリ検索パスにない場合は、ライブラリへのフルパスを指定できます。
  * `extra_paths`: デフォルトの動的リンカのものに加えて、MPIライブラリを検索するための追加のディレクトリを示します。
  * `mpiexec`: MPIランチャー実行可能ファイル。デフォルトは`mpiexec`ですが、一部のクラスターではスケジューラランチャーインターフェース（例: Slurmの`srun`、PBSの`aprun`）を使用する必要があります。特定のコマンドラインオプションを含めるために[`Cmd`オブジェクト](https://docs.julialang.org/en/v1/manual/running-external-programs/#Cmd-Objects)を渡すことも可能です。
  * `abi`: MPIライブラリのABI。デフォルトでは、[`identify_abi`](@ref)を使用して自動的に決定されます。現在サポートされている値については[`abi`](@ref)を参照してください。
  * `vendor`: `nothing`またはベンダー名（例えば`"cray"`）のいずれかです。`vendor`が"cray"の値を持つ場合、`cc --cray-print-opts=all`の出力がCrayコンパイララッパーによってリンクされるライブラリを解析するために使用されます。`mpi_gtl_*`が存在する場合、この.soがプリロードに追加されることに注意してください。また、`library_names`への入力はコンパイララッパーによって使用されるライブラリ名で上書きされます。
  * `export_prefs`: `true`の場合、`LocalPreferences.toml`ではなく`Project.toml`に設定をエクスポートします。
  * `force`: `true`の場合、すでに設定されている場合でも設定が行われます。
