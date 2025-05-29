```
LZ4FrameCompressor(; kwargs...)
```

LZ4圧縮コーデックを作成します。

# キーワード

  * `blocksizeid::BlockSizeID=default_size`: `max64KB`、`max256KB`、`max1MB`、または`max4MB`または`default_size`
  * `blockmode::BlockMode=block_linked`:  `block_linked`または`block_independent`
  * `contentchecksum::Bool=false`: `true`の場合、フレームは解凍されたデータの32ビットチェックサムで終了します
  * `frametype::FrameType=normal_frame)`:  `normal_frame`または`skippable_frame`
  * `contentsize::Integer=0`: 解凍されていないコンテンツのサイズ（不明な場合は0）
  * `blockchecksum::Bool=false`: `true`の場合、各ブロックの後にブロックの圧縮データのチェックサムが続きます
  * `compressionlevel::Integer=0`: 圧縮レベル（-1..12）
  * `autoflush::Bool=false`: `true`の場合、常にフラッシュします
