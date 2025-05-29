`register_compression!(db::DB, (comp, decomp); do_codec_checks=true)`

`compress(TEXT)::BLOB` および `decompress(BLOB)::TEXT` SQL 関数を `db` SQLite データベースに登録します。これらは、提供された圧縮器 `comp` と復元器 `decomp` を使用して、Julia 関数 `TranscodingStreams.transcode` を適用します。

  * `db`: `SQLite.jl` または互換性のある SQLite データベース
  * `(comp, decomp)`: `TranscodingStreams` コーデック、例: `(ZstdCompressor, ZstdDecompressor)`
  * `do_codec_checks`: 提供されたコーデックに対して健全性および一貫性チェックを実行するかどうか
