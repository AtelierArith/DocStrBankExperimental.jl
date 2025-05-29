```
ReadStatMeta <: AbstractMetaDict
```

`ReadStat`で処理されたデータファイルに関連付けられたファイルレベルのメタデータのコレクションです。

メタデータは、`DataAPI.jl`と互換性のあるメソッドを介して関連する[`ReadStatTable`](@ref)から取得および変更できます。`ReadStatMeta`を直接操作するための辞書のようなインターフェースも利用可能です。

# フィールド

  * `row_count::Int`: `ReadStat`パーサーによって返される行数; メタデータに利用できない場合は`-1`; データファイル内の実際の行数ではなく、`row_limit`パーサーオプションで設定された値を反映する場合があります。
  * `var_count::Int`: `ReadStat`パーサーによって返されるデータ列の数。
  * `creation_time::DateTime`: ファイル作成のタイムスタンプ。
  * `modified_time::DateTime`: ファイル変更のタイムスタンプ。
  * `file_format_version::Int`: ファイルフォーマットのバージョン番号。
  * `file_format_is_64bit::Bool`: 64ビットファイルフォーマットのインジケーター; SASにのみ関連します。
  * `compression::readstat_compress_t`: ファイル圧縮モード; 特定のファイルフォーマットにのみ関連します。
  * `endianness::readstat_endian_t`: データファイルのエンディアン。
  * `table_name::String`: データテーブルの名前; `.xpt`フォーマットにのみ関連します。
  * `file_label::String`: データファイルのラベル。
  * `file_encoding::String`: データファイルの文字エンコーディング。
  * `notes::Vector{String}`: データファイルに添付されたノート。
  * `file_ext::String`: データファイルのファイル拡張子。
