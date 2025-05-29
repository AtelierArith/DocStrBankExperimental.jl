```
IndexDefinition(;
    prefix=[],
    filter="",
    language_field="",
    language="",
    score_field="",
    score=1.0,
    payload_field="",
    index_type=IndexType.HASH
) -> IndexDefinition
```

IndexDefinitionは、HashまたはJsonの更新に対する自動インデックス作成のためのインデックス定義を定義するために使用されます。

# キーワード

  * `prefix::AbstractArray{AbstractString}`: インデックスがどのキーをインデックスすべきかを示します。各プレフィックスは`:`で終わる必要があります。
  * `filter::AbstractString`: 完全なRediSearch集約式言語を使用したフィルター式。
  * `language_field::AbstractString`: 設定されている場合、ドキュメントの属性として使用されるべき文書言語を示します。
  * `language::AbstractString`: 設定されている場合、インデックス内のドキュメントのデフォルト言語を示します。デフォルトは英語です。
  * `score_field::AbstractString`: 設定されている場合、ユーザーのランキングに基づいてドキュメントのランクとして使用されるべきドキュメント属性を示します。ランキングは0.0から1.0の間でなければなりません。設定されていない場合、デフォルトスコアは1です。
  * `score::Float64`: 設定されている場合、インデックス内のドキュメントのデフォルトスコアを示します。デフォルトスコアは1.0です。
  * `payload_field::AbstractString`: 設定されている場合、ドキュメントに対してバイナリセーフなペイロード文字列として使用されるべきドキュメント属性を示します。これは、カスタムスコアリング関数によってクエリ時に評価されるか、クライアントに取得されることができます。
  * `index_type::Number`: 現在、HASH（デフォルト）およびJSONをサポートしています。
