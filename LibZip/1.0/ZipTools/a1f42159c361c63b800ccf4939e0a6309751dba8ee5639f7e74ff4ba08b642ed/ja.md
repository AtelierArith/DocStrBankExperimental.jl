```
ZipFile
```

[`ZipArchive`](@ref) に含まれるファイルを表します。

## フィールド

  * `body::Vector{UInt8}`: ファイル内容のバイナリ表現。
  * `name::String`: ファイル名。
  * `index::Int64`: ファイルインデックス番号（ゼロベース）。
  * `size::Int64`: ファイルの非圧縮サイズ。
  * `comp_size::Int64`: ファイルの圧縮サイズ。
  * `time::DateTime`: ファイルの最終修正時間。
  * `crc::Int64`: ファイルのCRC-32チェックサム。
  * `comp_method::Int64`: ファイルの圧縮方法。
  * `encryption_method::Int64`: ファイルの暗号化方法。
