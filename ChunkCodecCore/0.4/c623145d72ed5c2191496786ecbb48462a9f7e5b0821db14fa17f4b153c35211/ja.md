```
abstract type Codec
```

エンコードされたデータをデコードするために必要な情報。

プロパティは読み取り用に公開されています。

タイプ `T <: Codec` が実装する必要があるメソッド：

  * `decode_options(::T)::DecodeOptions`

実装するためのオプションメソッド：

  * `can_concatenate(::T)::Bool`: デフォルトは `false`。
