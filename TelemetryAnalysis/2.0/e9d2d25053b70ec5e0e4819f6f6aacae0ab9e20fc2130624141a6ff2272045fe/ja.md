```
struct TelemetryVariableDescription
```

テレメトリデータベース内の変数を説明します。

# フィールド

  * `alias::Union{Nothing, Symbol}`: 変数のエイリアス。
  * `default_view::Symbol`: 処理中にこの変数のデフォルトビューを選択します。利用可能なオプションのリストについては、[`process_telemetries`](@ref)を参照してください。 (**デフォルト** = `:processed`)
  * `dependencies::Union{Nothing, Vector{Symbol}}`: この変数の処理された値を取得するために必要な依存関係のリストを含むベクター。`nothing`の場合、この変数には依存関係がありません。
  * `description::String`: 変数に関する説明。
  * `endianess::Symbol`: 変数のエンディアンを示すための`:littleendian`または`:bigendian`。
  * `label::Symbol`: 変数ラベル。
  * `position::Int`: アンパックされたテレメトリフレーム内の変数の位置。
  * `size::Int`: 変数のバイト数。
  * `btf::Function`: テレメトリフレームから変数のバイト配列データを取得するためのビット転送関数。
  * `rtf::Function`: バイト配列から生の値を取得するための生転送関数。
  * `tf::Function`: 処理された値を取得するための転送関数。
