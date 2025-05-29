```
ReadStatColMeta <: AbstractMetaDict
```

`ReadStat`で処理されたデータ列に関連付けられた変数レベルのメタデータのコレクションです。

メタデータは、`DataAPI.jl`と互換性のあるメソッドを介して関連する[`ReadStatTable`](@ref)から取得および変更できます。`ReadStatColMeta`を直接操作するための辞書のようなインターフェースも利用可能ですが、メタデータの値を変更することはできません。メタデータを取得および変更する別の方法は、[`colmetavalues`](@ref)を介して行うことです。

# フィールド

  * `label::String`: 変数ラベル。
  * `format::String`: 変数フォーマット。
  * `type::readstat_type_t`: `ReadStat`によって認識される元の変数タイプ。
  * `vallabel::Symbol`: 変数に関連付けられた値ラベルの辞書の名前; このフィールドを変更することの効果については、[`getvaluelabels`](@ref)も参照してください。
  * `storage_width::Csize_t`: データファイル内の変数のストレージ幅。
  * `display_width::Cint`: 表示用の幅。
  * `measure::readstat_measure_t`: 変数の測定タイプ; SPSSにのみ関連します。
  * `alignment::readstat_alignment_t`: 変数の表示揃え。
