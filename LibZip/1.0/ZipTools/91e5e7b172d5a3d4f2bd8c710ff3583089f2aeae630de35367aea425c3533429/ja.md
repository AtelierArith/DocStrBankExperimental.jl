```
ZipArchive
```

読み書き用のzipアーカイブを表す型。

## フィールド

  * `archive_ptr::Ptr{LibZipT}`: Cライブラリzip構造体へのポインタ。
  * `source_ptr::Ptr{LibZipSourceT}`: Cライブラリソース構造体へのポインタ。
  * `comment::String`: アーカイブのコメント。
  * `source_data::Vector{Vector{UInt8}}`: アーカイブのためのメモリ内ソースデータバッファを保持するコンテナ。
  * `closed::Bool`: アーカイブが閉じているかどうかを示すフラグ。
