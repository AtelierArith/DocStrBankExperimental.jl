`register_compression!(db::DB, (comp, decomp); do_codec_checks=true)`

Register `compress(TEXT)::BLOB` and `decompress(BLOB)::TEXT` SQL functions in the `db` SQLite database. They apply the Julia function `TranscodingStreams.transcode` with provided compressor `comp` and decompressor `decomp`.

  * `db`: SQLite database from `SQLite.jl` or compatible
  * `(comp, decomp)`: `TranscodingStreams` codecs, e.g. `(ZstdCompressor, ZstdDecompressor)`
  * `do_codec_checks`: whether to perform sanity and consistency checks on provided codecs
