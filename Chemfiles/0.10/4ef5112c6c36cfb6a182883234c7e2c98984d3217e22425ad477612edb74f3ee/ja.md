```julia
Trajectory(path::AbstractString) -> Chemfiles.Trajectory
Trajectory(
    path::AbstractString,
    mode::Char
) -> Chemfiles.Trajectory
Trajectory(
    path::AbstractString,
    mode::Char,
    format::AbstractString
) -> Chemfiles.Trajectory

```

指定された`path`の軌道ファイルを開きます。

オープニング`mode`は、読み取り用の`'r'`、書き込み用の`'w'`、または追加用の`'a'`で、デフォルトは`'r'`です。オプションの`format`パラメータは、ファイルを開くときに使用する特定のファイル形式を指定します。
